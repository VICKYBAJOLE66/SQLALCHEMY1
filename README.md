# SQLALCHEMY1
SECOND PROGRAM
SQLAlchemy simplifies the connection between Python and SQL databases by automatically converting Python class calls into SQL statements. This allows developers to use Python to access and work with databases, and not write separate SQL queries.
#import sqlalchemy second program
#vicky k bajole
from sqlalchemy import *
from sqlalchemy.orm import declarative_base, sessionmaker
DB_URL="mysql://root:root@localhost:3306/db2"
ENG=create_engine(DB_URL)
print(ENG)

Base=declarative_base()

class Student(Base):
    __tablename__="studentvicky"
    rn=Column(Integer,primary_key=True)
    name=Column(String(32))
    marks=Column(Float)
Base.metadata.create_all(ENG)
print("Table created")
Session= sessionmaker(bind=ENG)
sess=Session()
S1=Student(rn=7,name="abcd", marks=10.0)
S2=Student(rn=8,name="defg", marks=20.0)
S3=Student(rn=9,name="ghij", marks=30.0)
sess.add(S1)
sess.add_all([S2,S3])
sess.commit()
print("Object Inserted")

