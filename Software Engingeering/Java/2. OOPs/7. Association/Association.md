- [[Java]]
- [[OOP]]
## Description 
Defines the connection between, two classes that are set up through their objects 
![[Association.canvas|Association]]
## Types of association
- **one-to-one**: E.g. a person can have only one passport 
- **one-to-many**:  E.g. if we talk about the association between a Collage  and Student , a Collage can have many students.
- **many-to-one**: E.g. a state can have several cities, and those cities are related to that single state. 
- **many-to-many**: E.g. a single student can associate with multiple teachers, and multiple students can also be associated with a single teacher. 
## Example code
```java
import java.util.*;   
 class Mobile {    
    private String mobile_no;  
    
    public String getMobileNo() {  
        return mobile_no;  
    }  
    public void setMobileNo(String mobile_no) {  
        this.mobile_no = mobile_no;  
    }  
}  
class Person {       
    private String name;  
    List<Mobile> numbers;  
    public String getName() {  
        return name;  
    }  
    public void setName(String name) {  
        this.name = name;  
    }  
    public List<Mobile> getNumbers() {  
        return numbers;  
    }  
    public void setNumbers(List<Mobile> numbers) {  
        this.numbers = numbers;  
    }  
}  
public class AssociationExample {  
      public static void main(String[] args) {  
            Person person = new Person();  
            person.setName("Shubham Rastogi");  
             
           Mobile number1 = new Mobile();  
            number1.setMobileNo("8868923136");  
            Mobile number2 = new Mobile();  
            number2.setMobileNo("8630023310");  
      
            List<Mobile> numberList = new ArrayList<Mobile>();  
            numberList.add(number1);  
            numberList.add(number2);  
            person.setNumbers(numberList);  
            System.out.println(person.getNumbers()+" are mobile numbers of the person "+  
            person.getName());  
        }  
        
 }  
```
 