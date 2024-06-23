#Annotations
## Core Spring Boot Annotations

| Annotation                 | Description                                                                                                           | Example                                                                                       |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `@SpringBootApplication`   | Combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`. Used to mark the main class.             | <pre lang="java">@SpringBootApplication&#13;public class Application {&#13;    public static void main(String[] args) {&#13;        SpringApplication.run(Application.class, args);&#13;    }&#13;}</pre> |
| `@Configuration`           | Indicates that the class contains `@Bean` definitions. Used for Java-based configuration.                            | <pre lang="java">@Configuration&#13;public class AppConfig {&#13;    @Bean&#13;    public MyService myService() {&#13;        return new MyService();&#13;    }&#13;}</pre> |
| `@EnableAutoConfiguration` | Enables Spring Boot’s auto-configuration mechanism, automatically configuring the application based on dependencies. | <pre lang="java">@EnableAutoConfiguration&#13;public class MyApplication {&#13;    public static void main(String[] args) {&#13;        SpringApplication.run(MyApplication.class, args);&#13;    }&#13;}</pre> |
| `@ComponentScan`           | Tells Spring to scan for components, configurations, and services in the specified package.                           | <pre lang="java">@ComponentScan(basePackages = "com.example.myapp")&#13;public class AppConfig {&#13;}</pre> |


## Dependency Injection and Component Scanning Annotations

| Annotation       | Description                                                                                                           | Example                                                                                       |
|------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `@Autowired`     | Used for automatic dependency injection. Can be applied to constructors, fields, and methods.                         | <pre lang="java">@Autowired&#13;private MyService myService;</pre>                             |
| `@Qualifier`     | Used along with `@Autowired` to specify which bean to inject when multiple beans of the same type are present.         | <pre lang="java">@Autowired&#13;@Qualifier("myServiceImpl")&#13;private MyService myService;</pre> |
| `@Component`     | Indicates that a class is a Spring component.                                                                          | <pre lang="java">@Component&#13;public class MyComponent { ... }</pre>                           |
| `@Service`       | A specialization of `@Component`, used to denote service-layer classes.                                               | <pre lang="java">@Service&#13;public class MyService { ... }</pre>                               |
| `@Repository`    | A specialization of `@Component`, used to denote repository or DAO classes.                                            | <pre lang="java">@Repository&#13;public class MyRepository { ... }</pre>                         |

## Web Layer (MVC/REST) Annotations

| Annotation         | Description                                                                                                           | Example                                                                                       |
|--------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `@RestController`  | A convenience annotation that combines `@Controller` and `@ResponseBody`. Used to create RESTful web services.         | <pre lang="java">@RestController&#13;public class MyRestController { ... }</pre>                |
| `@Controller`      | Indicates that a class serves the role of a controller in Spring MVC.                                                  | <pre lang="java">@Controller&#13;public class MyController { ... }</pre>                         |
| `@RequestMapping`  | Maps HTTP requests to handler methods of MVC and REST controllers. Can be applied at class and/or method level.        | <pre lang="java">@RequestMapping("/api")&#13;public class MyController { ... }</pre>             |
| `@GetMapping`      | Maps HTTP GET requests onto specific handler methods.                                                                  | <pre lang="java">@GetMapping("/resource")&#13;public ResponseEntity<Resource> getResource() { ... }</pre> |
| `@PostMapping`     | Maps HTTP POST requests onto specific handler methods.                                                                 | <pre lang="java">@PostMapping("/resource")&#13;public ResponseEntity<Resource> createResource() { ... }</pre> |
| `@PutMapping`      | Maps HTTP PUT requests onto specific handler methods.                                                                  | <pre lang="java">@PutMapping("/resource/{id}")&#13;public ResponseEntity<Resource> updateResource(@PathVariable Long id, @RequestBody Resource resource) { ... }</pre> |
| `@DeleteMapping`   | Maps HTTP DELETE requests onto specific handler methods.                                                               | <pre lang="java">@DeleteMapping("/resource/{id}")&#13;public ResponseEntity<Void> deleteResource(@PathVariable Long id) { ... }</pre> |
| `@PatchMapping`    | Maps HTTP PATCH requests onto specific handler methods.                                                                | <pre lang="java">@PatchMapping("/resource/{id}")&#13;public ResponseEntity<Resource> patchResource(@PathVariable Long id, @RequestBody Map<String, Object> updates) { ... }</pre> |

## Bean Definition and Configuration Annotations

| Annotation     | Description                                                                                                           | Example                                                                                       |
|----------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `@Bean`        | Indicates that a method produces a bean to be managed by the Spring container. Used in `@Configuration` classes.      | <pre lang="java">@Bean&#13;public MyService myService() { ... }</pre>                          |
| `@Value`       | Used to inject property values into fields, methods, and constructors. Reads values from properties files or environment variables. | <pre lang="java">@Value("${myapp.service.url}")&#13;private String serviceUrl;</pre>           |
| `@PropertySource` | Specifies the properties file to be loaded. Used in `@Configuration` classes.                                         | <pre lang="java">@PropertySource("classpath:application.properties")&#13;@Configuration&#13;public class AppConfig { ... }</pre> |

## Exception Handling Annotations

| Annotation           | Description                                                                                                           | Example                                                                                       |
|----------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `@ControllerAdvice`  | Used to define a global exception handler for all controllers. Allows centralized exception handling.                 | <pre lang="java">@ControllerAdvice&#13;public class GlobalExceptionHandler {&#13;    @ExceptionHandler(value = { Exception.class })&#13;    public ResponseEntity<Object> handleAnyException(Exception ex, WebRequest request) {&#13;        // Handle exception and return ResponseEntity&#13;    }&#13;}</pre> |

## Data Access Layer (JPA/Hibernate) Annotations

| Annotation              | Description                                                                                                           | Example                                                                                       |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| `@Entity`                | Specifies that the class is an entity and is mapped to a database table. Used in JPA entities.                        | <pre lang="java">@Entity&#13;public class User { ... }</pre>                                   |
| `@Table`                 | Specifies the table in the database with which the entity is mapped. Can be used in conjunction with `@Entity`.        | <pre lang="java">@Entity&#13;@Table(name = "users")&#13;public class User { ... }</pre>         |
| `@Id`                    | Specifies the primary key of an entity. Used in JPA entities.                                                          | <pre lang="java">@Id&#13;@GeneratedValue(strategy = GenerationType.IDENTITY)&#13;private Long id;</pre> |
| `@GeneratedValue`        | Specifies how the primary key should be generated. Used in conjunction with `@Id` in JPA entities.                    | <pre lang="java">@Id&#13;@GeneratedValue(strategy = GenerationType.IDENTITY)&#13;private Long id;</pre> |
| `@Column`                | Specifies the mapping for a column in a database table. Used to customize column name, type, nullable, etc.          | <pre lang="java">@Column(name = "full_name", nullable = false)&#13;private String fullName;</pre> |
| `@ManyToOne`             | Specifies a many-to-one relationship between two entities. Used in JPA entities.                                      | <pre lang="java">@ManyToOne&#13;@JoinColumn(name = "department_id")&#13;private Department department;</pre> |
| `@OneToMany`             | Specifies a one-to-many relationship between two entities. Used in JPA entities.                                      | <pre lang="java">@OneToMany(mappedBy = "department")&#13;private List<Employee> employees;</pre> |
| `@ManyToMany`            | Specifies a many-to-many relationship between two entities. Used in JPA entities.                                     | <pre lang="java">@ManyToMany&#13;@JoinTable(name = "student_course",&#13;    joinColumns = @JoinColumn(name = "student_id"),&#13;    inverseJoinColumns = @JoinColumn(name = "course_id"))&#13;private List<Course> courses;</pre> |
| `@OneToOne`              | Specifies a one-to-one relationship between two entities. Used in JPA entities.                                       | <pre lang="java">@OneToOne(mappedBy = "user")&#13;private UserProfile userProfile;</pre>      |
| `@JoinColumn`            | Specifies the column that is used for joining an entity association or element collection. Used in conjunction with relationship annotations. | <pre lang="java">@ManyToOne&#13;@JoinColumn(name = "department_id")&#13;private Department department;</pre> |
| `@NamedQuery`            | Defines a named query. Used to declare queries in entity classes using JPQL (Java Persistence Query Language) query.   | <pre lang="java">@NamedQuery(name = "User.findByUsername",&#13;    query = "SELECT u FROM User u WHERE u.username = :username")</pre> |
| `@NamedNativeQuery`      | Defines a native SQL query. Used to declare native SQL queries in entity classes. Suitable when you need to execute complex SQL queries that are specific to your database schema and cannot be easily expressed in JPQL. | <pre lang="java">@NamedNativeQuery(name = "User.findByUsernameNative",&#13;    query = "SELECT * FROM users WHERE username = :username",&#13;    resultClass = User.class)</pre> |
| `@Query`                 | Defines a custom query to be executed by the repository. Supports JPQL and native SQL queries. This annotation allows you to define custom queries directly on repository methods in Spring Data JPA. It supports both JPQL and native SQL queries. | <pre lang="java">@Query("SELECT u FROM User u WHERE u.username = :username")&#13;User findByUsername(String username);</pre> |

