[[ETHICAL-HACKING]]


# WHAT IS SQL INJECTION?
SQL INJECTION IS ONE OF THE MAIN METHODS HACKERS USE TO RETRIEVE DATA, SUCH AS PASSWORDS, CREDIT CARDS OR SOCIAL SECURITY NUMBERS FROM DATABASES. THIS IS DONE BY INJECTING MALICIOUS SQL CODE IN THE DATABASE
TYPICALLY, HACKERS USE ..'.. TO BREAK THE SQL AND THEN WRITE SOMETHING SUCH AS
' OR 1=1-- TO BYPASS THE LOGIN FORM AND GET DIRECT ACCESS TO THE USER PROFILE. THE OUTCOME IS DESTRUCTIVE.

## HOW TO DEFEND FROM IT?
THERE ARE SEVERAL WAYS HOW TO PROTECT OUR WEBSITE FROM SQL INCJECTIONS
FIRSTLY, WE HAVE TO UNDERSTAND THAT PROGRAMMING LANGUAGES TALK TO DATABASE SERVERS USING DATABASE DRIVERS. STANDARTISING THESE DRIVERS IS THE KEY TO PROTECTING OURSELVES FROM THE MALICIOUS ATTACK.
IN JAVA
```java
// Connect to the database.
Connection conn = DriverManager.getConnection(URL, USER, PASS);

// Construct the SQL statement we want to run, specifying the parameter.
String sql = "SELECT * FROM users WHERE email = ?";

// Generate a prepared statement with the placeholder parameter.
PreparedStatement stmt = conn.prepareStatement(sql);

// Bind email value into the statement at parameter index 1.
stmt.setString(1, email);

// Run the query...
ResultSet results = stmt.executeQuery(sql);

while (results.next())
{
    // ...do something with the data returned.
}
```

USING RUBY ON RAILS, HOWEVER, SHOWS ANOTHER METHOD, THE USAGE OF OBJECT RELATIONAL MAPPING. USING THIS METHOD DEVELOPERS HARDLY EVER HAVE TO WRITE ANY SEQUEL STATEMENTS IN THEIR CODE.

```ruby

def current_user(email)
  # The 'User' object is an Active Record object, that has find methods 
  # auto-magically generated by Rails.
  User.find_by_email(email)
end
```

ESCAPING THE INPUTS AND QUOTIENTS IS CRUCIAL. HASHING THE PASSWORDS IS A SECOND HAND SECURITY MEASSURE THAT NEEDS TO BE TAKEN EITHER WAY, LET THE SQL INJECTION WORK OR NOT.


