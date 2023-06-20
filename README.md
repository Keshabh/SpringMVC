# SpringMVC
1. A sub framework of spring Framework to build web based applications. 
2. Build on top of servlet api.
3. Follows Model View Controller(MVC) Design Pattern i.e a way to organize code in the project.
4. Implements all basic features of core spring like IOC(Inversion of Control), Dependency Injection, e.t.c;

## Steps:
1. Download Tomcat zip file and extract it, and it to eclipse server as projects run time environment.
2. create a maven project(web), and the structure should be java, resources, webapp inside src/main folder.
3. Dispatcher Servlet: handles incoming HTTP requests and sends it to appropriate controller.
4. View resolver: It takes the view name returned by controller, resolves it by looking into its directory and returns the required views file.
5. Add spring-web-mvc dependency in pom.xml file.
6. configure dispatcher servlet in web.xml as following:
   <servlet>
  	<servlet-name>spring</servlet-name>
  	<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
  </servlet>
  
  <servlet-mapping>
  	<servlet-name>spring</servlet-name>
  	<url-pattern>/</url-pattern>
  </servlet-mapping>
#it means to accept url of all types.
7. Now create a spring-servlet.xml file inside views folder only, where spring-servlet.xml is a convention name based on the servelt name "spring" given in web.xml while configurig dispatcher servlet.
8. In spring-servlet.xml, we specifiy the controllers that needs to be redirected to after getting URL and also view resolver too.
9. create a controller, return a view(create a jsp view in views folder).

## Sending data from Controller to View
1. There is 2 way to do it:
2. One is Model and another is ModelAndView
3. In case of Model , we use Model.addAttribute(key,value), we return view name.
4. In case of ModelAndView, we use Model.addObject(key,value) and model.setViewName(viewName) and we return ModelAndView object.
5. in view page, we can use <% Integer val = (Integer)request.getAttribute(roll) %> and <h1><%=val%>, to retrieve the values and use it.
6. Another way to retrieve data in view page is to make use of expression language as ${roll}.
7. And to further implement jstl library, we can add its dependency, and import it in the view page.

## Sending data from View to Controller
1. Create a form and provide an action path and method too as "POST", both in form as well as in controller.
2. create its controller to retrieve the data.
3. There are multiple ways to retrieve the data.
4. first is HttpServletResponse request, here we use request.getParamter("name").
5. second is RequestParam annotation, where we can fetch the values in the parameter iself.
6. third is, ModelAttribute annotation, where we just have to specify have a object of a class, whose data will be mapped directly to the returned data.
7. To pass common data in every view page, we can create a function with ModelAttribute annotation, which will run everytime berfore any other fucntion runs.
