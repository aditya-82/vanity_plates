#This is the Vanity Plates project from Week 2 of the CS50 Python course available online from Harvard. The program needs to identify valid vanity plate inputs with the following restrictions:
#All vanity plates must start with at least two letters.”
#“… vanity plates may contain a maximum of 6 characters (letters or numbers) and a minimum of 2 characters.”
#“Numbers cannot be used in the middle of a plate; they must come at the end. For example, AAA222 would be an acceptable … vanity plate; AAA22A would not be acceptable. The first number used cannot be a ‘0’.”
#“No periods, spaces, or punctuation marks are allowed.”

import string
def main():
    # Ask for input
    plate = input("Proposed plate number: ")
    #Check if string length is valid
    ans1 = check_len(plate)
    if ans1 == 1:
        print("Invalid")
    else:
        #Check for punctuation
        ans2 = check_punct(plate)
        if ans2 == 1:
            print("Invalid")
        else:
            ans3 = char_check(plate)
            if ans3 == 0:
                print("Valid")
            else:
                print("Invalid")
    
def check_len(a):
    l = len(a)
    if 2 <= len(a) <= 6:
        return 0
    else:
        return 1

def check_punct(b):
    for i in b:
        if i not in string.punctuation:
            continue
        else:
            return 1
            break

def char_check(c):
    if c[0].isalpha() == False or c[1].isalpha() == False:
        return 1
    else:
        if len(c) == 6:
            if c[2].isnumeric() == True and int(c[2]) != 0 and c[3].isnumeric() == True and c[4].isnumeric() == True and c[5].isnumeric() == True:
                return 0
            elif c[3].isnumeric() == True and int(c[3]) != 0 and c[4].isnumeric() == True and c[5].isnumeric() == True:
                return 0
            elif c[4].isnumeric() == True and int(c[4]) != 0 and c[5].isnumeric():
                return 0
            elif c[5].isnumeric() == True and int(c[5]) != 0:
                return 0
            elif c.isalpha() == True:
                return 0
            else:
                return 1    
        elif len(c) == 5:
            if c[2].isnumeric() == True and int(c[2]) != 0 and c[3].isnumeric() == True and c[4].isnumeric() == True:
                return 0
            elif c[3].isnumeric() == True and int(c[3]) != 0 and c[4].isnumeric() == True:
                return 0
            elif c[4].isnumeric() == True and int(c[4]) != 0:
                return 0
            elif c.isalpha() == True:
                return 0
            else:
                return 1    

        elif len(c) == 4:
            if c[2].isnumeric() == True and int(c[2]) != 0 and c[3].isnumeric() == True:
                return 0
            elif c[3].isnumeric() == True and int(c[3]) != 0:
                return 0
            elif c.isalpha() == True:
                return 0
            else:
                return 1    
        elif len(c) == 3:
            if c[2].isnumeric() == True and int(c[2]) != 0:
                return 0
            elif c.isalpha() == True:
                return 0
            else:
                return 1    
        elif len(c) == 2:
            return 0
    
main()
