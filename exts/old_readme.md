 木Muxi犀
==

	a python web framework
		~simple and powerful~

<hr/>
## GET Muxi

	pip install muxi

## First Muxi Project
at First, you need to go to terminal, and init your muxi project!

	$ muxi init MuxiExample

init will automatically create muxi application :) <br/>


                |-app/  -----------| __init__.py
                |-test/            |
	MuxiExample-|-manage.py        | views.py
                |-requirement.txt  | forms.py
                |-README.md        | templates
                |                  | static

and Then, open app/views.py, and write views(sth you want to response)

	from . import app

	@url(app, '/muxi')
	def muxi():
		return "<h1>Hello Muxi</h1>"

now, you can run your muxi app

	$ python manage.py runserver

this muxi app running on http://127.0.0.1:3044/muxi
<hr>

#### simple and  powerful !

## Debug Mode

	DebugToolbar

[learn_more]()

## Muxi Cli(command)
you can use ~muxi~ cli to create, init, deploy your project and help you register<br/>
isolate APP. the simplest way to learn muxi cli is the --help option:

	$ muxi --help

[learn_more]()

## URL & Redirect
in muxi, you can use function_name(or endpoint) to build URL
:ex:

	@url(app, '/index')
	def index():
		return {}

	gen_url("index") --> /index
	gen_url("index", name="muxi") --> /index?name=muxi

you can use the :function:redirect: and gen_url to go to the specific url

	redirect(gen_url("index")) -go-to-> /index
	redirect("/index") -go-to-> /index

[learn_more]()

## HTTP-Request-Session
you can use global <code>request</code> to get the WSGI environ
:ex:

	from muxi import request

	url: http://127.0.0.1:3044/muxi?name="neo1218"

	request.args.get(name) ==> "neo1218"
	request.cookies ==> return cookies dict {}

will, you can also use global <code>session</code> to store sth

	from muxi import session

	session["username"] = "neo1218"
	session["id"] = 1

[learn more](#)

## Front-end Template
muxi use jinja2 as font-end template <br/>
you can use ~@views~ to add jinja template in your Response, and <br/>
use dict to push sth into jinja
:app/views.py:

	from . import app

	@url(app, "/muxi")
	@views("muxi.html")
	def muxi():
		return {"name" = "muxi"}

:app/templates/muxi.html:

	<html>
		<body>
		<h1>I love {{ name }} !</h1>
		</body>
	</html>

[learn more]()

## Form System
muxi integrate with WTForms <br/>
:ex:

	from muxi.form import Form
	from muxi.form.fields import StringField, SubmitField
	from muxi.form.validators import Required

	class MuxiForm(Form):
		body = StringField(validators=[Required()])
		submit = SubmitField("submit")

and now, you can create a form object in your views function and <br/>
pass this form to jinja(the html file)

[learn more]()

## SQL ORM
muxi use sqlalchemy as SQL ORM. <br/>
what you need todo is create 'app/models.py' and coding

	from muxi import db

	class User(db.Model):
		coding...

[learn_more]()

## DataBase
create migration floder to record database migrate

	python manage.py db init

create database and first migrate

	python manage.py db migrate -m "some note"

update database

	python manage.py db upgrade

teardown database

	config this option:
	app.config['SQLALCHEMY_COMMIT_ON_TEARDOWN'] = True

	and the database would be automatically teardown when sth oops...

[learn_more]()

## NoSql DataBase

## Isolate App

## Manage Muxi Project
muxi use manage.py script to manage your muxi project, you can see:<br/>
we can use manage to run your project and create & update your database and<br/>
get into shell, and deploy your project

	you can also config the ~manage.py~ script file by yourself :)

[learn_more]()

## Admin Site

## Rest API

### LICENSE::MIT

	see [license](https://github.com/neo1218/muxi/blob/master/LICENSE) for more detail

### :About Name:

	The original meaning of 木犀(muxi) is {{ a sweet-scented osmanthus }} and
	used as my :team name ~ MuxiStudio:
	beacause I love my team, so I chose muxi as this web framework's name

![muxi](http://7xj431.com1.z0.glb.clouddn.com/slogan_bg.png)
