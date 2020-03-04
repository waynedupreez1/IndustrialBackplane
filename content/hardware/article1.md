Title: Seriously WTForm
Date: 2014-06-28 10:42
Category: Hardware
Author: Wayne du Preez
icon: pied-piper-alt

I'm about neck deep into a large Flask application. It's an MVP so no over the top
Angular frontend or anything. Means I'm using a lot of WTForm to get user input...

Means I'm saying ***"WTF?!"***  **a lot!**<br>
I've used WTForms before. In django projects as well. I've never really felt so bitter
toward them. The name just used to be funny... now I'm seriously wondering "what the fuck?!".
It's not hard to get data to Flask views. It's actually pretty freaking simple. So the only
reason to use an extension like WTForms is because it would simplify this even further.

Except it doesn't. **Not at first**.

A little work has to go in to get the most from the library but that little work does go
a long way. I'll show you a few ways you can get WTForms to really speed up your form
generation and digestion.

Let's look at a simple form class definition:
```python
class Person(Form):
    firstname = TextField(u'First Name', [Required(),Length(max=64)])
    middlename = TextField(u'Middle Name', [Optional(),Length(max=64)])
    lastname = TextField(u'Last Name', [Required(),Length(max=64)])
    email = EmailField(u'Email', [Email(), Optional()])
    dob = DateField(u'Date of Birth', [Optional()], format='%m/%d/%Y')
    phone = IntegerField(u'Phone No.', [Optional()], default=None)
    gender = SelectField(u"Gender", choices=[(1, 'Male'), (2, 'Female')])
```

<br>
That corresponds to a model `Person`:
```python
class Person(db.Model):

  __tablename__ = 'persons'

  id = Column(db.Integer, primary_key=True)
  firstname = Column(db.String(64))
  middlename = Column(db.String(64))
  lastname = Column(db.String(64))
  email = Column(db.String(64))
  phone = Column(db.Integer)
  dob = Column(db.DateTime)
  created_time = Column(db.DateTime, default=get_current_time)
  gender = Column(db.Integer)
```