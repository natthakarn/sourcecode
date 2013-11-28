sourcecode
==========
head = """
<!DOCTYPE html>
<html>
<body>
<center>
<h1>HTML Student</h1>
<p>Data Student</p>
"""
tail = """
</body>
</html>
"""
table = """
<table border="5">
</center>
"""
ID = []
Firstname = []
Lastname = []
Year = []
Sex = []
	
def main():
	Student_list()
	Student_data()
	
def Student_list():
	temp = ""
	File = open('std_list.csv')
	for i in File:
		i = i.strip()
		words = i.split(",")
		ID.append(words[0])
		Firstname.append(words[1])
		Lastname.append(words[2])
		Year.append(words[3])
		Sex.append(words[4])
	temp += '<tr> <td><center> '+ Firstname[0]+'</center></td> <td><center>'+ Lastname[0] +'</center></td> </tr>'
	for i in range(1,len(Year)):
		temp += '<tr> <td><center><a href = '+ Firstname[i] +'.html >'+Firstname[i]+'</a></center></td><td><center>'+ Lastname[i] +'</center></td> </tr>' 	
	temp += '</table>'	
	try:
   		
    	   f = open('list.html', 'w')
    	   try:
        	f.write(head) 
        	f.write(table)
        	f.write(temp)
        	f.write(tail)
    	   finally:
        	f.close()
	except IOError:
    		pass

def Student_data():
	for i in range (0,len(Year)):
		f = open(''+Firstname[i]+'.html','w')
		std = ""
		std += head
		std += table
		std += '<tr> <td><center> '+ ID[0]+'</center></td> <td><center>'+ Firstname[0] +'</center></td> <td><center>'+Lastname[0]+'</center></td> <td><center>'+Year[0]+'</center></td> <td><center>'+Sex[0]+'</center></td> </tr>'
		std += '<tr> <td><center> '+ID[i]+'</center></td> <td><center>'+ Firstname[i] +'</center></td> <td><center>'+Lastname[i]+'</center></td> <td><center>'+Year[i]+'</center></td> <td><center>'+Sex[i]+'</center></td> </tr>'
		std += '</table>'
		std += tail
		f.write(std)

if __name__ == "__main__":
	main()


