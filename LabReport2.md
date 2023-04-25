# Part 1: StringServer

Code for StringServer: 
![Image](one.png)

Attached are two runs with the `/add-message` query.
![Image](two.png)
In this screenshot, the main method runs when the port is being created for the server. The arguments for the main method are the String[] args array. The port number I used is 4600. Then, the Server.start method from the Server file is called and opens the server up using the parseInt of args[0] and a new Beginner class object. The next method to be called is handleRequest, whose argument is a url of type URI, which will analyze the contents of the URL and more specifically the query. This run updates the string somp to include "Hello", so it is up to now "Hello" since this was the first run.

![Image](three.png)
In this screenshot, the server is running so the main method is not called, because the main method serves to open the server but we are still using the same one. The first method to be called is handleRequest, whose URI url object is now updated to the current URL shown in the above. This run updates the string somp to include "HOLA", so somp is now "\n + Hello + \n + HOLA".

# Part 2: Debugging

Test that works: 
```
@Test
  public void testAvgWithoutLowestt() {
    double[] input = {6.0,2.0,7.0};
    assertEquals(6.5,ArrayExamples.averageWithoutLowest(input),1.0);
  }
```

Test that doesn't work at first:
```
 @Test
  public void testAvgWithoutLowest() {
    double[] inputt = {6.0,8.0,2.0,2.0,4.0};
    assertEquals(6.0,ArrayExamples.averageWithoutLowest(inputt),1.0);
  }
  ```
  
Symptom: (the top test which expects a value of 6.0 is the one that's failing and producing the symptom) 

  
Code before debugging:
```
static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
```
