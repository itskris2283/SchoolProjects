from tkinter import *
import mysql.connector as c
import tkinter.messagebox as tmsg
from datetime import *

try:
    con=c.connect(host="localhost",user="root",passwd="123456",database="pysql")
    cur=con.cursor()
except:
    tmsg.showerror("Error","Invalid Database Credentials")
root=Tk()
root.geometry("900x450")
root.resizable(False,False)
root.configure(bg="light yellow")
root.title("Books Management System")
def show():
    
    cur.execute("select * from book")
    data=cur.fetchall()
    
    screen=Toplevel(root)
    screen.geometry("800x450")

    #scrollbar=Scrollbar(screen)
    #scrollbar.pack(fill=Y,side=RIGHT)
    
    num=2
    for i in data:
        name=Label(screen,text=i[0],font="helvetica 16 bold",fg="blue")
        name.grid(row=num,column=0,padx=10,pady=10)

        num=num+1
    screen.mainloop()

heading=Label(root,text="Books Management System",fg="#57a1f8",font=('Microsoft YaHei UI Light',20))
heading.pack()

def insert():
    bid=book_id.get()
    title=book_title.get()
    author=book_author.get()
    pub=publisher.get()
    gen=genre.get()
    isbnval=isbn.get()
    priceval=price.get()

    today=date.today()
    str_date=str(today)

    try:
        if bid=="" or title=="" or author=="" or pub=="" or gen=="" or isbnval=="" or priceval=="":
            tmsg.showinfo("Insertion Status","All Fields is required")

        elif bid=="Enter Book ID" or title=="Enter Book Title" or author=="Enter Author Name" or pub=="Enter Book Publisher" or gen=="Enter Book Genre" or isbnval=="Enter Book ISBN" or priceval=="Enter Book Price":
            tmsg.showinfo("Insertion Status","All Fields is required")
            
        else:
            cur.execute("insert into book values('"+bid+"','"+title+"','"+author+"','"+pub+"','"+gen+"','"+isbnval+"','"+priceval+"','"+str_date+"')")
            tmsg.showinfo("Insert Status","Inserted Successfully")
            con.commit()
    except Exception as e:
        print(e)
        tmsg.showerror("Error","Invalid Entries")
def update():
    bid=book_id.get()
    title=book_title.get()
    author=book_author.get()
    pub=publisher.get()
    gen=genre.get()
    isbnval=isbn.get()
    priceval=price.get()

    if bid=="" or title=="" or author=="" or pub=="" or gen=="" or isbnval=="" or priceval=="":
        tmsg.showinfo("Update Status","All Fields is required")
    else:
        update_query="update book set book_title='"+title+"',book_author='"+author+"',publisher='"+pub+"',genre='"+gen+"',isbn='"+isbnval+"',price='"+priceval+"'"
        cur.execute(update_query)
        con.commit()
        tmsg.showinfo("Update Status","Updation successfull")

def delete():
    try:
        if (book_id.get()==""):
            tmsg.showerror("Delete Status","Enter valid Book Id")
        else:
            cur.execute("delete from book where book_id='"+book_id.get()+"'")
            tmsg.showinfo("Delete Status","Deletion Successful")
            con.commit()
    except:
        tmsg.showerror("Error","Invalid Book Id")
        

def create():
    try:
        query="create table Book (Book_ID int primary key,Book_Title varchar(30),Book_Author varchar(50),publisher varchar(50),genre varchar(30),isbn int(15),price int(5),Date date)"
        cur.execute(query)
    except:
        print("")
        
def exiit():
    root.destroy()

##book id---
def on_enter(e):
    book_id.delete(0,'end')

def on_leave(e):
    if book_id.get()=="":
        book_id.insert(0,"Enter Book ID")

book_id=Entry(root,width=15,bg="light yellow",fg="black",font=('Microsoft YaHei UI Light',15),border=0)
book_id.place(x=60,y=60)

book_id.bind("<FocusIn>",on_enter)
book_id.bind("<FocusOut>",on_leave)

book_id.insert(0,"Enter Book ID")
Frame(root,width=180,height=2,bg='black').place(x=55,y=90)
#------------------------------------------------------------
def on_enter(e):
    book_title.delete(0,'end')

def on_leave(e):
    if book_title.get()=="":
        book_title.insert(0,"Enter Book Title")
##title
book_title=Entry(root,width=15,bg="light yellow",fg="black",font=('Microsoft YaHei UI Light',15),border=0)
book_title.place(x=60,y=150)

book_title.bind("<FocusIn>",on_enter)
book_title.bind("<FocusOut>",on_leave)

book_title.insert(0,"Enter Book Title")
Frame(root,width=180,height=2,bg='black').place(x=55,y=180)
#-------------------------------------------------------
def on_enter(e):
    book_author.delete(0,'end')

def on_leave(e):
    if book_author.get()=="":
        book_author.insert(0,"Enter Author Name")
#author
book_author=Entry(root,width=18,bg="light yellow",fg="black",font=('Microsoft YaHei UI Light',15),border=0)
book_author.place(x=60,y=250)

book_author.bind("<FocusIn>",on_enter)
book_author.bind("<FocusOut>",on_leave)

book_author.insert(0,"Enter Author Name")
Frame(root,width=185,height=2,bg='black').place(x=55,y=280)
#-----------------------------------------------
def on_enter(e):
    publisher.delete(0,'end')

def on_leave(e):
    if publisher.get()=="":
        publisher.insert(0,"Enter Book Publisher")
        
#publisher
publisher=Entry(root,width=18,bg="light yellow",fg="black",font=('Microsoft YaHei UI Light',15),border=0)
publisher.place(x=55,y=350)

publisher.bind("<FocusIn>",on_enter)
publisher.bind("<FocusOut>",on_leave)

publisher.insert(0,"Enter Book Publisher")
Frame(root,width=185,height=2,bg='black').place(x=55,y=380)
#-------------------------------------------------
def on_enter(e):
    genre.delete(0,'end')

def on_leave(e):
    if genre.get()=="":
        genre.insert(0,"Enter Book Genre")
#genre
genre=Entry(root,width=18,bg="light yellow",fg="black",font=('Microsoft YaHei UI Light',15),border=0)
genre.place(x=280,y=60)

genre.bind("<FocusIn>",on_enter)
genre.bind("<FocusOut>",on_leave)

genre.insert(0,"Enter Book Genre")
Frame(root,width=185,height=2,bg='black').place(x=280,y=90)
#--------------------------------------------------
def on_enter(e):
    isbn.delete(0,'end')

def on_leave(e):
    if isbn.get()=="":
        isbn.insert(0,"Enter Book ISBN")

#isbn
isbn=Entry(root,width=18,bg="light yellow",fg="black",font=('Microsoft YaHei UI Light',15),border=0)
isbn.place(x=280,y=150)

isbn.bind("<FocusIn>",on_enter)
isbn.bind("<FocusOut>",on_leave)

isbn.insert(0,"Enter Book ISBN")
Frame(root,width=185,height=2,bg='black').place(x=280,y=180)
#-----------------------------------
def on_enter(e):
    price.delete(0,'end')

def on_leave(e):
    if price.get()=="":
        price.insert(0,"Enter Book Price")

#price
price=Entry(root,width=18,bg="light yellow",fg="black",font=('Microsoft YaHei UI Light',15),border=0)
price.place(x=280,y=250)

price.bind("<FocusIn>",on_enter)
price.bind("<FocusOut>",on_leave)

price.insert(0,"Enter Book Price")
Frame(root,width=185,height=2,bg='black').place(x=280,y=280)
#---------------------------------------------

##buttons
insert_button=Button(text="Insert",width=20,cursor="hand2",bg="black",command=insert,fg="white",font=('Microsoft YaHei UI Light',15))
insert_button.place(x=580,y=60)

show_button=Button(text="Show Records",width=20,cursor="hand2",bg="black",command=show,fg="white",font=('Microsoft YaHei UI Light',15))
show_button.place(x=580,y=130)

update_button=Button(text="Update",width=20,cursor="hand2",bg="black",command=update,fg="white",font=('Microsoft YaHei UI Light',15))
update_button.place(x=580,y=200)

create_button=Button(text="Delete Record",width=20,cursor="hand2",bg="black",command=delete,fg="white",font=('Microsoft YaHei UI Light',15))
create_button.place(x=580,y=270)

delete_button=Button(text="Exit",width=20,cursor="hand2",bg="black",command=exiit,fg="white",font=('Microsoft YaHei UI Light',15))
delete_button.place(x=580,y=340)
#----------------------------------------------------------
create()

root.mainloop()
