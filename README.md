# Text-file-encryptor
This project is to encrypt a text file using Caesar cipher method.

Here's the code

import os,shutil
dire=os.getcwd()
listOfFile=os.listdir(dire)
print 'Press Enter to quit'
while True:
    EncryptionValue=int(5)
    plainFile=raw_input("Enter filename:")
    if plainFile == "":
        break
    if plainFile in listOfFile and plainFile.endswith('.txt'):
        inputFile=plainFile
        unEncryptFile='unEncrypted.txt'
        shutil.copy(plainFile,unEncryptFile)
        TextFile=open(plainFile,'r')
        plainText=TextFile.read()
        cipherText=''
    
        for ch in plainText:
            ordValue=ord(ch)
            cipherValue=ordValue + EncryptionValue
            if cipherValue > ord('z'):
                cipherValue=ord('a') + EncryptionValue-\
                            (ord("z") - ordValue + 1)
            cipherText += chr(cipherValue)
    
        TextFile.close()
        TextFile=open(plainFile,'w')
        TextFile.write(str(cipherText))
        TextFile.close()
        newFileName=raw_input("Save unencrypted file as:")
        if newFileName.endswith('.txt') and newFileName not in listOfFile  :
            os.rename(unEncryptFile,newFileName)
            print 'Encryption successful!!!...'

        elif not newFileName.endswith('.txt'):
            print 'Save file as text format.Re-Enter file name.'
        elif newFileName in listOfFile:
            print 'This file name already exists!'
    elif plainFile not in listOfFile:
        print "Entry doesn't exist in current working directory."
    elif not plainFile.endswith('.txt'):
        print 'Invalid entry.'
    
      
    
    
            
    
