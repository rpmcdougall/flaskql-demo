# flaskql-demo
Graphene/SQLAlchemy Demo on Flask

https://docs.graphene-python.org/projects/sqlalchemy/en/latest/tutorial/

https://github.com/alexisrolland/flask-graphene-sqlalchemy/wiki/Flask-Graphene-SQLAlchemy-Tutorial


Paste into python terminal started from project root to add some sample data
```
from models import engine, db_session, Base, Department, Employee
Base.metadata.create_all(bind=engine)

engineering = Department(name='Engineering')
db_session.add(engineering)
hr = Department(name='Human Resources')
db_session.add(hr)

peter = Employee(name='Peter', department=engineering)
db_session.add(peter)
roy = Employee(name='Roy', department=engineering)
db_session.add(roy)
tracy = Employee(name='Tracy', department=hr)
db_session.add(tracy)
db_session.commit()
```

Sample Query - localhost:5000/graphql to access query browser or point GraphQL Playground to the same url.
```
query{
  allEmployees(sort: name_desc) {
    edges {
      node {
        id
        name
        department {
          name
        }
      }
    }
  }
}
```