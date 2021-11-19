#file management 

import os   # importing os we can read file and we can check extension


folderpath=r"/boot/2020aashupbl"    #r is a leading character
os.chdir(folderpath)

os.getcwd()   #check current working directory

#to  check files we have now 
os.listdir()

#get extension

list_extension=[]
for file in os.listdir():
  extension=file.split(".")[-1]       # splited based on extension
  list_extension.append(extension)
print(list_extension)

#importing shutil to remove file or folder if it is already there

import shutil

newpath=folderpath + '_'  + "pbl_creation"   

try:
  shutil.rmtree(newpath)
  os.mkdir(newpath)
except:
  os.mkdir(newpath)

print(newpath)

#transfer file in specific folder

for ext in list_extension:
  print(ext,end=',')
  os.makedirs(newpath + "/" + ext)
  for file in os.listdir():
    if ext in file:
      try:
        shutil.copy(file,newpath + "/" + ext)  #for remove use move()
      except:
        print('discard')

print("congrats you created")
