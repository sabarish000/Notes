# Few points to remember
## Mapping an Entity with Native SQL Queries and Joins
When mapping an entity in Spring Data JPA for a native SQL query that involves joins, you typically have two approaches:
### Approach 1: Use **@SqlResultSetMapping:**

This approach is suitable when your native SQL query returns columns from multiple tables due to joins, and you want to map the result directly to an entity or a DTO (Data Transfer Object).

1) Define the @SqlResultSetMapping:
```java
import javax.persistence.*;

@SqlResultSetMapping(
    name = "UserDetailMapping",
    entities = {
        @EntityResult(
            entityClass = User.class,
            fields = {
                @FieldResult(name = "id", column = "user_id"),
                @FieldResult(name = "username", column = "username"),
                // Map other fields of User entity here
            }
        ),
        @EntityResult(
            entityClass = Department.class,
            fields = {
                @FieldResult(name = "departmentId", column = "dept_id"),
                @FieldResult(name = "departmentName", column = "dept_name"),
                // Map other fields of Department entity here
            }
        )
    }
)
```
2) Apply @NamedNativeQuery with @SqlResultSetMapping:
```java
@NamedNativeQuery(
    name = "UserDetailNativeQuery",
    query = "SELECT u.id as user_id, u.username, d.id as dept_id, d.name as dept_name " +
            "FROM users u " +
            "JOIN departments d ON u.department_id = d.id " +
            "WHERE u.id = :userId",
    resultSetMapping = "UserDetailMapping"
)

```
### Approach 2: Map to a DTO or Custom Projection:

If the query result does not map directly to an existing entity, or if you want more control over the result set, you can map the result to a DTO (Data Transfer Object) or a custom projection.
1) Create a DTO or Custom Projection:
```java
   public class UserDetailDto {

    private Long userId;
    private String username;
    private Long departmentId;
    private String departmentName;

    // Getters and setters
    // Constructors if needed
}
```
2) Use @Query with Constructor Expression:
```java
@Query(value = "SELECT u.id as userId, u.username, d.id as departmentId, d.name as departmentName " +
               "FROM users u " +
               "JOIN departments d ON u.department_id = d.id " +
               "WHERE u.id = :userId",
       nativeQuery = true)
List<UserDetailDto> getUserDetailsByUserId(@Param("userId") Long userId);
```
