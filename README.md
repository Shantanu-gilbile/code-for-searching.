# code-for-searching.

#Creation of list.
def creation():
    global listc
    listc = []
    students = int(input("Enter the number of students : "))
    for i in range(students):
        rollno = int(input("Enter the rollno of students : "))
        listc.append(rollno)
    print(listc)

#Linear Searching.
def linearSearching(listc,f):
    for i in  range (len(listc)):
        if f==listc[i]:
            print(f"The Rollno {f} is Present at index {[i]}.")
            break
    else:
        print(f"Roll no {f} is Absent.")

#Sentinel Searching
def sentinelSearch(listc,  f):
    n = len(listc)
    last = listc[n - 1]
    listc[n - 1] = f
    i = 0
    while (listc[i] != f):
        i += 1
    listc[n - 1] = last
    if ((i < n - 1) or (listc[n - 1] == f)):
        print(f"The Rollno {f} is Present at index {[i]}")
    else:
        print(f"Roll no {f} is Absent.")

#Binary Searching.
def binarySearch(listc, f):
    first = 0
    last = len(listc) - 1
    while first <= last:
        mid = (first + last) // 2
        if listc[mid] < f:
            first = mid + 1
        elif listc[mid] > f:
            last = mid - 1
        else:
            return mid
    return -1

#Fibnocci Searching.
def fibnocciSearch(listc):
    n = len(listc)
    fib2 = 0
    fib1 = 1
    fibM = fib2 + fib1

    while (fibM < n):
        fib2 = fib1
        fib1 = fibM
        fibM = fib2 + fib1
    offset = -1
    
    while (fibM > 1):
        i = min(offset + fib2, n - 1)
        if (listc[i] < f):
            fibM = fib1
            fib1 = fib2
            fib2 = fibM - fib1
            offset = i
        elif (listc[i] > f):
            fibM = fib2
            fib1 = fib1 - fib2
            fib2 = fibM - fib1
        else:
            return i

        if (fib1 and listc[n - 1] == f):
            return n - 1
        return -1

#Menu driven program.
print("1.Linear Searching.\n2.Sentinal Searching.\n3.Binary Searching.\n4.fibnocci Searching.\n5.Exit.")

while True :
    ch=int(input("Enter the Choice : "))
    if ch==1:
        creation()
        f = int(input("Enter the rollno you want to find : "))
        linearSearching(listc, f)

    elif ch==2:
        creation()
        f = int(input("Enter the rollno you want to find : "))
        sentinelSearch(listc, f)

    elif ch==3:
        creation()
        f = int(input("Enter the rollno you want to find : "))
        result = binarySearch(listc, f)
        if result != -1:
            print(f"The rollno {f}  is Present.")
        else:
            print(f"The roll no {f} is Absent")

    elif ch==4:
        creation()
        f = int(input("Enter the rollno you want to find : "))
        res = fibnocciSearch(listc)
        if res >= 0:
            print(f"Roll no {f} is Present.")
        else:
            print(f"The roll no {f} is Absent.")

    elif ch==5:
        print("Thank you !")
        break
        
    else :
        print("Invalid choice.")
