# FLASK Blog

Tutorial from [Corey Shafer - WebApp Tutorial](https://youtu.be/MwZwr5Tvyxo)

## Installation of flask

### Jinja
[Jinja2](http://jinja.pocoo.org/docs/2.10/faq/#how-compatible-is-jinja2-with-django)

### Forms stuff

```
pip3 install flask-wtf
```

### Bootstrap
[Bootstrap template includes](https://getbootstrap.com/docs/3.3/getting-started/)

### Alchemy
SQLAchemy is a DB layer ORM (Object Relational Mapping) that encapsulates the DB vendor implementation.

```
pip3 install flask-sqlalchemy
```

in your python code do the import as follows:
```
from flask_sqlalchemy import SQLAlchemy
...

app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///site.db'

# get a database instance
db = SQLAlchemy(app)
```
Now define the db structure - and then afterwards create the Database as follows:

```py
python3
>>> from flaskblog import db
>>> db.create_all()
```
After creating the DB you can add "stuff" to the DB:
```
>>> from flaskblog import User, Post
>>> user_1 = User(username='Soren', email='soren@arleth.net',password='password')
>>> db.session.add(user_1)
>>> db.session.commit()
>>> User.query.all()
>>> post_1 = Post(title='Blog Title from site.db',content='Blog content site.db', user_id=user_1.id)
>>> post_2 = Post(title='Blog Title 2 from site.db',content='Blog content 2 site.db', user_id=user_1.id)
>>> db.session.add(post_1)
>>> db.session.add(post_2)
>>> db.session.commit()
```

## User handling

Register users, authentication etc

### Flask bcrypt
bcrypt is a an extension in Flask that enables hashing etc.
```
pip3 install flask-bcrypt
```

#### Testing bcrypt
```
python3
>>> from flask_bcrypt import Bcrypt
>>> bcrypt = Bcrypt()
>>> bcrypt.generate_password_hash('testing')
b'$2b$12$HxyjrzajhzZIITf4w2agE.rUPoxxpOOqHtj3IhxQZOYbUu.66.3VS'
>>> bcrypt.generate_password_hash('testing').decode('utf-8')
'$2b$12$cZpwSVpBlSZaaOFkOanMjuyrLVjgd3pqPf.Y9PzLA.QdwmnaGqpWm'
>>> hashed_pw = bcrypt.generate_password_hash('testing').decode('utf-8')
>>> bcrypt.check_password_hash(hashed_pw, 'password')
False
>>> bcrypt.check_password_hash(hashed_pw, 'testing')
True
>>>
```

### Flask Log In
Flask extension
```
pip3 install flask-login
```

### Flask picture handling
Pillow - install it using pip
```
pip3 install Pillow
```
