1. Create a Class in Models Package (Note: Class name is PascalCase, singular, and a noun)

-------

2. Class Template
```

import java.util.Date;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.FetchType;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.JoinColumn;
import javax.persistence.ManyToOne;
import javax.persistence.OneToMany;
import javax.persistence.PrePersist;
import javax.persistence.PreUpdate;
import javax.persistence.Table;
import javax.validation.constraints.Min;
import javax.validation.constraints.NotNull;
import javax.validation.constraints.Size;

import org.springframework.format.annotation.DateTimeFormat;

//////////////////////////////////////////////////////////////
//	OBJECT CLASS
//////////////////////////////////////////////////////////////

@Entity
@Table(name="objects")
public class Objects {

	//	//// FIELDS //////////////////////////////////////////
	
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private long id;
	
	@Column(updatable=false)		// this will not allow createdAt to be updated after creation
	@DateTimeFormat(pattern="yyyy-MM-dd")
	private Date createdAt;
	
	@DateTimeFormat(pattern="yyyy-MM-dd")
	private Date updatedAt;
	
	@PrePersist
	protected void onCreate()	{
		this.createdAt = new Date();
	}
	
	@PreUpdate
	protected void onUpdate() {
		this.updatedAt = new Date();
	}
	
	//	//// CONSTRUCTORS ////////////////////////////////////

	public Dojo() {
	}


	//	//// GETTERS AND SETTERS /////////////////////////////
	
}
```

---------------------------------

3. Name Column
```
@NotNull
@Size(min=1, max=255, message="name must be at least one character in length")
private String Name;
```

---------------------------------

4. Age Column
```
@NotNull
@Min(value=1, message="Age must be at least 1")
private long age;
```

5. One to Many Relationship (Relationship: One dojo to Nany Ninja)
```
@OneToMany(mappedBy="dojo", fetch = FetchType.LAZY)
private List<Ninja> ninjasList;
```

6. Many to One Relationship (Relationship: Many Ninja to One Dojo)
```
@ManyToOne( fetch = FetchType.LAZY )
@JoinColumn( name="dojo_id" )
private Dojo dojo;
```

----------------------------------

5. MAKE SURE TO MAKE GETTERS AND SETTERS