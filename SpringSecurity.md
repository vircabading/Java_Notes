# Spring Security Set Up

## Dependency
```
<!-- DEPENDENCIES FOR SPRING SECURITY -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

------------------------------------------

## User Class
```
/** ******************************************************
 * 	Users Class 
 */

@Entity
@Table(name="users")
public class User {
    
	//	**** FIELDS **************************************
	
    @Id
    @GeneratedValue
    private Long id;
    private String username;
    private String password;
    @Transient
    private String passwordConfirmation;
    @Column(updatable=false)
    private Date createdAt;
    private Date updatedAt;
    
    // **** Many-To-Many Relationship ********************
    @ManyToMany(fetch = FetchType.EAGER)
    @JoinTable(
        name = "users_roles", 
        joinColumns = @JoinColumn(name = "user_id"), 
        inverseJoinColumns = @JoinColumn(name = "role_id"))
    private List<Role> roles;
    
    //	**** CONSTRUCTORS ********************************
    
    public User() {
    }
    
    //	**** GETTERS AND SETTERS *************************
}
```

------------------------------------------