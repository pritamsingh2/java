## Student.java
package com.mile1.bean;

public class Student {
	
	public Student()
	{
	}
	

	public Student(String name,int[] marks) 
	{
		// TODO Auto-generated constructor stub
	}

	
       
		String name;
		int[] marks= new int[3];
		
		public String getName() {
			return name;
		}
		public void setName(String name) {
			this.name = name;
		}
		public int[] getMarks() {
			return marks;
		}
		public void setMarks(int[] marks) {
			this.marks = marks;
		}
	
}


## null marks array exception

package com.mile1.exception;

public class NullMarksArrayException extends Exception {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}
	public String toString()  {
	
	return "NullMarksArrayException occurred" ;
	}
}


## null name Exception
package com.mile1.exception;

public class NullNameException extends Exception {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}
	public String toString()  
	{
		return "NullNameException occurred"; 
	}

}


## null student exception
package com.mile1.exception;

public class NullStudentException extends Exception {

	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}
	public String toString()  {
		
		return "NullStudentException occurred" ;
	}

}


## studentMain.java

package com.mile1.main;

import com.mile1.bean.Student;
import com.mile1.exception.NullMarksArrayException;
import com.mile1.exception.NullNameException;
import com.mile1.exception.NullStudentException;
import com.mile1.service.StudentService;

public class StudentMain {
	
	public static void main (String a []) {
	 	StudentService studentService = new StudentService ();	
	    StudentReport studentReport = new StudentReport ();
		System.out.println (" Grades Calculation: ");
		String x = null;
		for (int i = 0; i < data.length; i++) 
		{
			try 
			{
				x = studentReport.validate (data [i]);
			} 
			catch (NullNameException e) 
			{
				x="NullNameException occurred";	
			} 
			catch (NullMarksArrayException e) 
			{
				x="NullMarksArrayException occurred";
			}
			catch (NullStudentException e) 
			{ 
				x="NullStudentException occurred "; 
			}
			System.out.println ("GRADE="+x);
		}
		System.out.println ("Number of Objects with Marks array as null ="+ studentService.findNumberOfNullMarks (data));
		System.out.println ("Number of Objects with Name as null="+ studentService.findNumberOfNullNames(data));	
		System.out.println ("Number of Objects that are entirely null="+ studentService.findNumberOfNullObjects(data));
	  }
	static	Student data[] = new Student[4];
	static{
		
		for (int i = 0; i < data.length; i++) 	
			data [i]= new Student();
	              
	data [0] = new Student("Sekar", new int[]{35,35,35});
	data [1] = new Student(null, new int[]{11,22,33});
	data [2] = null;
	data [3] = new Student("Manoj", null);
	}


}



## Studentreport.java

package com.mile1.main;

import com.mile1.bean.Student;
import com.mile1.exception.NullMarksArrayException;
import com.mile1.exception.NullNameException;
import com.mile1.exception.NullStudentException;

public class StudentReport  {

	
	public String findGrade(Student studentObject)
	{
		String z;
	
		int[] x= studentObject.getMarks();
		if(x[0]<35 || x[1]<35 || x[2]<35 )
		{
			z= "F";
		}
		
		else
		{
			int sum= x[0]+x[1]+x[2];
			if(sum<=150)
				z=  "D";
			else if(150 < sum & sum <= 200)
				z=  "C";
			else if(200 < sum & sum <=250)
				z=  "B";
			else 
				z=  "A";	
		}
		return z;
		
	}
	public String validate(Student studentObject)
	throws NullStudentException, NullNameException, NullMarksArrayException
	{
		
		int[] y= studentObject.getMarks();
		if (studentObject.equals(null)  )
		{
			throw new NullStudentException();
		}
		else {
			if(studentObject.getName()=="" || studentObject.getName()== null )
			{
				throw new NullNameException();
			}
		if( y== null)
		{
			throw new NullMarksArrayException();
	}
		}	
		String k;
		k=this.findGrade(studentObject);
		return k;
	}
}


## Student Service.java

package com.mile1.service;

import com.mile1.bean.Student;

public class StudentService {
	
	public int findNumberOfNullMarks(Student data[])
	{
	           int c= 0;
	           Student[] y= data;
	           if(y.equals(null))
	           {
	        	   c++;
	           }
	           return c;
	}
	public int findNumberOfNullNames(Student data [])
	{
		int d= 0;
        Student[] y= data;
        if(y.equals(null))
        {
     	   d++;
        }
        return d;
	                   
	}
	public int findNumberOfNullObjects(Student data [])
	{
		int e= 0;
        Student[] y= data;
        if(y.equals(null))
        {
     	   e++;
        }
        return e; 
	}



}

