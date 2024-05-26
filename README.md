--CAPSTONE PROJECT 1--
#Capstone Project 
#Project Data Karyawan
#Mohammad Rizky D 

program = True

dataKaryawan = {
    'EMP001': {
        'Name' : 'Iqbal R',
        'Position' : 'Head of Human Resource',
        'Age' : '34',
    },
    'EMP002': {
        'Name' : 'Fahmi A',
        'Position' : 'Head of Legal',
        'Age' : '32',
    },
    'EMP003': {
        'Name' : 'Rizky D',
        'Position' : 'Head of Finance',
        'Age' : '29',
    },
}
def tampilkanData():
    if(len(dataKaryawan)!=0 or len(dataKaryawan)<0):
        print ('List of Employees')
        Number = 1
        for i in dataKaryawan :
            print (f"{Number}. Code: {i}, Name: {dataKaryawan[i]['Name']}, Position: {dataKaryawan[i]['Position']}, Age: {dataKaryawan[i]['Age']}")
            Number+=1               
    else:
        print("****No Data****")

def tampilkanDataPilihan():
    inputKode = input("Input Employee Code: ")
    for i in dataKaryawan :
        print (f"Employee with Code: {inputKode}")

    if(inputKode in dataKaryawan):
        print (f"Code: {inputKode}, Name: {dataKaryawan[i]['Name']}, Position: {dataKaryawan[i]['Position']}, Age: {dataKaryawan[i]['Age']}")
    else:
        print("****No Employee Data****")

def createData():
    inputKode = input("Input Employee Code: ")

    if(inputKode in dataKaryawan):
        print("***Data Already Exist***")
    else:
        inputNama= input("Input Name: ")
        inputPosisi= input("Input Position: ")
        inputUmur= input("Input Age: ")

        dataTambahKaryawan = {
            inputKode : { 
                'Name': inputNama,
                'Position': inputPosisi,
                'Age' : inputUmur,
            }
        }

        while(True):    
            inputConfirm = input("Will the Data be Saved? (Y/N): ")
            inputConfirm = inputConfirm.upper()
                        
            if(inputConfirm=='Y'):
                dataKaryawan.update(dataTambahKaryawan)
                print("***Data is Saved***")
                tampilkanData()
                break
            elif(inputConfirm=='N'):
                print("***Data is NOT Saved***")
                break
            else:
                continue

def updateData():
    inputKode = input("Input the Employee Code to be Updated: ")
    while(True):
            inputConfirm = input("Press Y to continue your update OR Press N if you want to cancel it (Y/N): ")
            inputConfirm = inputConfirm.upper()

            if(inputConfirm == 'Y'):
                inputColumn = input("Input the Description to be Edited (Name/Position/Age): " )
                inputValue = input("Please Input the new Description to be Updated: ")

                while(True):
                    inputConfirm = input("Confirm the Data to be Updated? (Y/N): ")
                    inputConfirm = inputConfirm.upper()
                                
                    if(inputConfirm == 'Y'):
                        dataKaryawan[inputKode][inputColumn] = inputValue
                        print("***Data is Updated***")
                        tampilkanData()
                        break
                    elif(inputConfirm == 'N'):
                        print("***Data is NOT Updated***")
                        break
                    else:
                        continue
                break                    
            elif(inputConfirm == 'N'):
                print("***Data is NOT Updated***")
                break
            else:
                continue

def deleteData():
    inputKode = input("Input Employee Code: ")

    if(inputKode not in dataKaryawan):
        print("***Data does not Exist***")
    else:
        while(True):
            inputConfirm = input("Are you sure you want to delete it? (Y/N): ")
            inputConfirm = inputConfirm.upper()

            if(inputConfirm == 'Y'):
                del dataKaryawan[inputKode]
                print("***Data has been Deleted***")
                tampilkanData()
                break
            elif(inputConfirm == 'N'):
                print("***Data has NOT been Deleted***")
                break
            else:
                continue

#Start
while (program == True):
#Main Menu
    print ('''
        ---Adenan Corporation---

        List Menu:
        1. Employees Data
        2. Create Data
        3. Update Data
        4. Delete Data
        5. Exit (Main Menu)
    ''')

    menu = int(input("Please Input a number from 1 - 5): "))

#Read
    if(menu == 1):
        #Sub Menu 1
        while(True):
            print ('''
            +++++++List of Employees Data+++++++

            List Menu :
            1. All Employee Data
            2. Employee Data According to Code
            3. Back to Main Menu
            ''')

            menu = int(input("Please Input a number from 1 - 3: "))

            if(menu == 1):
                tampilkanData()

            elif(menu == 2):
                tampilkanDataPilihan()
            
            elif(menu == 3):
                break

            else:
                print("*****Please Input the Right Menu Number*****")

#Create
    elif(menu == 2): 
        while(True):
            print ('''
            +++++++Create Employee Data+++++++

            List Menu :
            1. Create Data
            2. Back to Main Menu
            ''')

            menu = int(input("Please Input a number from 1 - 2: "))

            if(menu == 1):
                createData()

            elif(menu == 2):
                break

            else:
                print("*****Please Input the Right Option Number*****")

#Update            
    elif(menu == 3):
        while(True):
            print ('''
            +++++++Update Employee Data+++++++

            List Menu :
            1. Update Employee Data
            2. Back to Main Menu
            ''')

            menu = int(input("Please Input the number from 1 - 2: "))

            if(menu == 1):
                updateData()

            elif(menu == 2):
                break
            else:
                print("*****Please Input 1 or 2*****")

#Delete
    elif(menu == 4):
        while(True):
            print ('''
            *****Delete Employee Data*****

            List Menu :
            1. Delete Employee Data
            2. Back to Main Menu
            ''')

            menu = int(input("Please Input the number from 1 - 2: "))

            if(menu == 1):
                deleteData()

            elif(menu == 2):
                break

            else:
                print("*****Please Input 1 or 2*****")

#Exit
    elif(menu == 5):
        print("Thank you and Good Bye!")
        program=False
    
    else :
        print("*****Please Input the Number between 1 to 5*****")
