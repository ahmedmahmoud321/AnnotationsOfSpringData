# AnnotationsOfSpringData


### **`mappedBy`** 

**mappedBy** should be in the side that not containing the foreign key

## Who Should Have the Foreign Key in a Relationship?

`in one to one` -> the owner should have the foreign key.

`in one to many` - > the many should have the foreign key.


**`mappedBy( argument )`** -> **the argument is the name of `current class reference` in the other class `as attribute name.`**


```java
public class User {
    @OneToOne(cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    @JoinColumn(name = "profile_id", referencedColumnName = "id")
    private Profile profile;
}
```

```java
public class Profile {
// the argument is reference to current in the other class... attribute name
    @OneToOne(mappedBy = "profile")
    private User user;
}
```




### `@JoinColumn`
the join column is the part who generate the foreign key by specifing the `"name = foreign_key_name"` and `referencedColumnName = id_name_in_original_entitiy`





* At the **`User`** Entitiy
this will create one to one relationship with the fetch lazy and the cascade all,

**the `@JoinColumn` the name is the properity that exist in the current class and created.**
so new properity `profile_id` will be created and refereced by the `id` that exist in the other entitiy `Profile`.



```java
public class User {
    @OneToOne(cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    @JoinColumn(name = "profile_id", referencedColumnName = "id")
    private Profile profile;
}
```

* Diagram

  ![image](https://github.com/user-attachments/assets/e7aea050-df9e-4d95-8144-a49c00bb7102)
