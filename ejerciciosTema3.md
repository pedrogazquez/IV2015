##Ejercicios 1: Darse de alta en algún servicio PaaS tal como Heroku, Nodejitsu, BlueMix u OpenShift. ##
Me he dado de alta en Heroku y en OpenShift como se puede ver en las siguientes imágenes:

![heroku](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202015-11-04%20112056_zpslltlhm7r.png)
![openshift](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202015-11-04%20112413_zpsm8s2etno.png)

##Ejercicios 2: Crear una aplicación en OpenShift y dentro de ella instalar WordPress. ##
Esta es la aplicación sencilla que he creado en wordpress dentro de OpenShift [aplicación en wordpress] (http://php-ejer2.rhcloud.com/). Aquí una captura:
![wordpress](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202015-11-06%20095758_zpsnafyfc5j.png)

##Ejercicios 3: Realizar una app en express (o el lenguaje y marco elegido) que incluya variables como en el caso anterior.##
Ya que mi proyecto lo estoy haciendo conunto con DAI, este ejercicio lo he hecho con una aplicación de Python con el micro framework Flask, mediante el cual uso varias variables para guardar usuarios mediante la ruta de la dirección como en el ejemplo. Esta es mi app, la cual tiene cuatro rutas distintas:
```
from wtforms import *
from flask import Flask, session, redirect, url_for, escape, request, render_template
import sys, pydoc
from HTMLParser import HTMLParser

reload(sys)
sys.setdefaultencoding('utf-8')
app = Flask(__name__)
#Expresion regular para que el numero de VISA sea corecto
regVISA='(\d\d\d\d)[ \-](\d\d\d\d)[ \-](\d\d\d\d)[ \-](\d\d\d\d)$'
listUsers = []
listSurna = []

class RegistrationForm(Form):
	username = TextField('Nombre: ', [validators.Length(min=4, max=25)])
	userap = TextField('Apellidos: ', [validators.Length(min=4, max=50)])
	email = TextField('Correo electronico', [validators.Length(min=6, max=35),validators.Required(),validators.Email(message='El email es incorrecto')])
	visaNum = TextField('Numero de VISA', [validators.Length(min=6, max=35),validators.Required(),validators.Regexp(regVISA, flags=0, message='Numero de VISA incorrecto')])
	nacimiento = DateField('Fecha de nacimiento: ', format='%Y-%m-%d')
	direccion = TextField('Direccion: ', [validators.Length(min=6, max=60)])
	password = PasswordField('Contrasenia', [validators.Required(),validators.EqualTo('confirm', message='La contrasenia debe coincidir con la repeticion')])
	confirm = PasswordField('Repite la contrasenia')
	accept_tos = BooleanField('Acepto las condiciones', [validators.Required()])
	formaPago = SelectField(u'Forma de pago', choices=[('contra', 'Contra reembolso'), ('visa', 'Tarjeta VISA')])

@app.route('/register', methods=['GET', 'POST'])
def register():
	form = RegistrationForm(request.form)
	if request.method == 'POST' and form.validate():
		return('Gracias %s por registrarte!' % form.username.data)
	return render_template('register.html', form=form)

@app.route('/users')
def showUsers():
	return 'Esta es la lista de usuarios registrados: ' + ',\n'.join(map(str,listUsers))

@app.route('/add/<username>')
def	addUser(username):
	listUsers.append(username)
	return 'Usuario registrado. Pruebe /users para ver los usuarios'

@app.route('/')
def index():
	form = RegistrationForm(request.form)
	return render_template('index.html', form=form)
	
if __name__ == '__main__':
    app.run(host='0.0.0.0',debug=True)  # 0.0.0.0 para permitir conexiones desde cualquier sitio. Ojo, peligroso en modo debug

```
Y aquí dos capturas añadiendo un usuario:

![add](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/ej8-2_zpskbysdgaa.png)

y mostrando los usuarios:

![user](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/ej3-2_zpspmqt8gtp.png)


##Ejercicios 4: Crear pruebas para las diferentes rutas de la aplicación. ##
He realizado pruebas para 

##Ejercicios 5: Instalar y echar a andar tu primera aplicación en Heroku.##
Para realzar este ejercicio lo primero que he hecho ha sido descargar el cinturón de herramientas de heroku con la siguiente línea:
```
wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh
```
Una vez hecho esto, hacemos *heroku login* con nuestros credenciales y después procedemos a hacer el clone para guardar el repositorio en nuestra carpeta local:
```
git clone https://github.com/heroku/python-getting-started.git
cd python-getting-started
```
Seguidamente procedemos a desplegar nuestra aplicación, primero hacemos el create que nos creará una aplicación con un nombre aleatorio si no le indicamos ningún nombre:
![create](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202015-11-14%20140100_zpsd8feyv9r.png)

Ahora desplegamos nuestro código con *git push heroku master*:
![push](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202015-11-14%20140903_zpswqazogve.png)

Después de hacer esto lo último que nos queda es abrir la aplicación con las siguientes órdenes:
```
heroku ps:scale web=1
heroku open
```
En mi caso el nombre aleatorio ha sido [pacific-garden-4019](https://pacific-garden-4019.herokuapp.com/):

![final](http://i1042.photobucket.com/albums/b422/Pedro_Gazquez_Navarrete/Captura%20de%20pantalla%20de%202015-11-14%20142852_zpsr8qiibdn.png)

##Ejercicios 6: Usar como base la aplicación de ejemplo de heroku y combinarla con la aplicación en node que se ha creado anteriormente. Probarla de forma local con foreman. Al final de cada modificación, los tests tendrán que funcionar correctamente; cuando se pasen los tests, se puede volver a desplegar en heroku.##


##Ejercicios 7: Haz alguna modificación a tu aplicación en node.js para Heroku, sin olvidar añadir los tests para la nueva funcionalidad, y configura el despliegue automático a Heroku usando Snap CI o alguno de los otros servicios, como Codeship, mencionados en StackOverflow ##


##Ejercicios 8: Preparar la aplicación con la que se ha venido trabajando hasta este momento para ejecutarse en un PaaS, el que se haya elegido. ##


