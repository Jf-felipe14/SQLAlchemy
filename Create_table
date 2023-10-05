# import the packages you will need
from sqlalchemy import create_engine,Column,Integer,String,Float,text
from sqlalchemy.orm import sessionmaker, declarative_base
import pandas as pd

base= declarative_base()

# declare the user, password , database and the host

db_user='root'
db_password='secret_password'
db_host='localhost'
engine = create_engine(f'mysql+pymysql://{db_user}:{db_password}@{db_host}/storage')

# create the Class/Table

class Tabela2(base):
    __tablename__='User'
    ID=Column(Integer, primary_key=True, autoincrement=True)
    nome=Column(String(50))
    idade=Column(Integer)
    
base.metadata.create_all(engine)

Session=sessionmaker(bind=engine)
session=Session()

# import a data to your table at Mysql
user=Tabela2(nome='Julio',idade=36)
session.add(user)
session.commit()

# using pandas to see weather the table/Database is working

query='''select * from User'''
df=pd.read_sql(query,engine)
df.head()
