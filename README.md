# Login-Page
Login Page using Python and the details will be collected in the background by using database.




from tkinter import *
from tkinter import messagebox
import ast

window=Tk()
window.title("signUp")
window.geometry('925x500+300+200')
window.configure(bg='#fff')
window.resizable(False,False)

def signup():
    username=user.get()
    password=code.get()
    new=new.get()

    if password==new:
        try:
            file=open('datasheet.txt','r+')
            d=file.read()
            r=ast.literal_eval(d)

            dict2=({username:password})
            r.update(dict2)
            file.truncate(0)
            file.close()

            file=open('datasheet.txt','w')
            w=file.write(str(r))

            messagebox.showinfo('signUp','Successfully signup')

        except:
            file=open('datasheet.txt','w')
            pp=str({username:password})
            file.write(pp)
            file.close()

    else:
        messagebox.showerror('Invalid','Password should match')


    

img = PhotoImage(file='D:\\Users\\JAZZ\\Documents\\Login Page')
Label(window,image=img,border=0,bg='white').place(x=50,y=90)

Frame=Frame(window,width=350,height=390,bg='#fff')  #//color//
Frame.place(x=480,y=50)

heading=Label(Frame,text='signUp',fg="#s7a1f8",bg='white',font=('Microsoft UI light',23,'bold'))
heading.place(x=100,y=5)

###------###

def on_enter(e):
    user.delete(0,'end')
def on_leave(e):
    if user.get()=='':
        user.insert(0,'Username')


user = Entry(Frame,width=25,fg='black',border=0,bg='white',font=('Microsoft UI light',11,))
user.Place(x=30,y=80)
user.insert(0,'Username')
user.blind("<FocusIn",on_enter)
user.blind("<FocusIn",on_leave)

Frame(Frame,width=295,height=2,bg='black').place(x=25,y=107)

###------###

def on_enter(e):
    code.delete(0,'end')
def on_leave(e):
    if code.get()=='':
        code.insert(0,'Password')


code = Entry(Frame,width=25,fg='black',border=0,bg='white',font=('Microsoft UI light',11,))
code.Place(x=30,y=150)
code.insert(0,'Password')
code.blind("<FocusIn",on_enter)
code.blind("<FocusIn",on_leave)

Frame(Frame,width=295,height=2,bg='black').place(x=25,y=177)

###--------###

Button(Frame,Width=39,pady=7,text='SignUp',bg='#57a1f8',fg='white',border=0,command=signup).place(x=35,y=280)
Label=Label(Frame,Text='I have an account',fg='black',bg='white',font=('Microsoft UI light',9))
Label.Place(x=90,y=240)

signin=Button(Frame,Width=6,text='Signin',border=0,bg='white',cursor='hand2',fg='#s7a1f8')
signin.place(x=200,y=240)
