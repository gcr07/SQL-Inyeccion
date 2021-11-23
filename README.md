# SQL-Inyeccion

<h2> 💻 Boolean-based blind SQL Injection 💻</h2>

<h3> SQLMap </h3> 

<strong> Type of atacks that SQL Map suports. The technique characters BEUSTQ refers to the following: </strong>


<ul>
<li>B: Boolean-based blind	</li>
<li>E: Error-based			</li>
<li>U: Union query-based	</li>
<li>S: Stacked queries		</li>
<li>T: Time-based blind		</li>		
<li>Q: Inline queries		</li>
</ul>

<h4> Boolean-based blind </h4>

<p> Boolean-based SQL injection is a technique which relies on sending an SQL query to the database. The result allows an attacker to judge whether the payload used returns true or false, even though no data from the database are recovered </p>

```sql
AND 1=1
```

<h4> Error-based </h4>

<p> Error-based SQL injection is an In-band injection technique where the error output from the SQL database is used to manipulate the data inside the database. In In-band injection, the attacker uses the same communication channel for both attacks and collect data from the database.</p>

```sql
AND GTID_SUBSET(@@version,0)
```


<h4> Union query based </h4>

<p> Union based SQL injection allows an attacker to extract information from the database by extending the results returned by the original query. The Union operator can only be used if the original/new queries have the same structure (number and data type of columns). </p> 

```sql

UNION ALL SELECT 1,@@version,3

```


<h4>Stacked queries</h4>

<p> Stacked queries provide a lot of control to the attacker. By terminating the original query and adding a new one, it will be possible to modify data and call stored procedures. This technique is massively used in SQL injection attacks and understanding its principle is essential to a sound understanding of this security issue.</p>

```sql

; DROP TABLE users

```
<h4>Time-based blind SQL Injection</h4>

<p> What is a time-based blind SQL injection? In a time-based SQL injection, the attacker sends SQL queries to the database, which force the database to wait for a specified amount of time before responding. ... This allows the attacker to know if the result is true or false, even though no data from the database is returned.</p>

```sql
AND 1=IF(2>1,SLEEP(5),0)

```
