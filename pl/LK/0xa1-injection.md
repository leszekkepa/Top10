# A1:2017 Wstrzyknięcie (Injection)

| Threat agents/Attack vectors | Security Weakness           | Wpływ               |
| -- | -- | -- |
| Access Lvl : Exploitability 3 | Prevalence 2 : Wykrywalność 3 | Technical 3 : Business |
| W zasadzie każde dane wejściowe can be an injection vector, environment variables, parameters, external and internal web services, and all types of users. [Injection flaws](https://www.owasp.org/index.php/Injection_Flaws) occur when an attacker can send hostile data to an interpreter. | Injection flaws are very prevalent, particularly in legacy code. Injection vulnerabilities are often found in SQL, LDAP, XPath, or NoSQL queries, OS commands, XML parsers, SMTP headers, expression languages, and ORM queries. Injection flaws are easy to discover when examining code. Scanners and fuzzers can help attackers find injection flaws. |Injection can result in data loss, corruption, or disclosure to unauthorized parties, loss of accountability, or denial of access. Injection can sometimes lead to complete host takeover. The business impact depends on the needs of the application and data.|


## Czy aplikacja jest podatna?

Aplikacja jest podatna na atak, jeśli:

* Dane dostarczane przez użytkownika nie są walidowane, filtrowane oraz odkażane/oczyszczane (sanitized) przez aplikację.
* Zapytania dynamiczne or non-parameterized calls without context-aware escaping are used directly in the interpreter.  
* Złośliwe dane są używane used within object-relational mapping (ORM) search parameters to extract additional, sensitive records.
* Złośliwe dane są  is directly used or concatenated, such that the SQL or command contains both structure and hostile data in dynamic queries, commands, or stored procedures.
* Some of the more common injections are SQL, NoSQL, OS command, Object Relational Mapping (ORM), LDAP, and Expression Language (EL) or Object Graph Navigation Library (OGNL) injection. The concept is identical among all interpreters. Source code review is the best method of detecting if applications are vulnerable to injections, closely followed by thorough automated testing of all parameters, headers, URL, cookies, JSON, SOAP, and XML data inputs. Organizations can include static source ([SAST](https://www.owasp.org/index.php/Source_Code_Analysis_Tools)) and dynamic application test ([DAST](https://www.owasp.org/index.php/Category:Vulnerability_Scanning_Tools)) tools into the CI/CD pipeline to identify newly introduced injection flaws prior to production deployment.

## Jak zapobiegać

Abyc zapobiec (injection) dane należy oddzielić od poleceń i zapytań (requires keeping data separate from commands and queries).

* Najlepszym wyborem będzie skorzystanie z safe API, co pozwoli uniknąc zupełnie interpretera or provides a parameterized interface, or migrate to use Object Relational Mapping Tools (ORMs). **Uwaga**: Nawer sparametryzowane procedury składowane wciąz mogą introduce SQL injection jeśli PL/SQL lub T-SQL będzie łączył zapytania lub dane, or executes hostile data with EXECUTE IMMEDIATE or exec().
* Use positive or "whitelist" server-side input validation. This is not a complete defense as many applications require special characters, such as text areas or APIs for mobile applications.
* For any residual dynamic queries, escape special characters using the specific escape syntax for that interpreter. **Uwaga**: SQL structure such as table names, column names, and so on cannot be escaped, and thus user-supplied structure names are dangerous. This is a common issue in report-writing software.
* Korzystaj z opcji LIMIT i innych poleceń SQL w zapytaniu, aby zapobiec ujawnieniu ogromniej ilości danych w razie wstrzyknięcia kodu SQL.

## Przykładowe scenariusze ataku 

**Scenariusz #1**: Aplikacja używa niezaufanych danych (untrusted data) do tworzenia podatnego wywołania zapytania (call) SQL:

`String query = "SELECT * FROM konta WHERE klientID='" + request.getParameter("id") + "'";`

**Scenariusz #2**: Aplikacja ślepo ufa (application’s blind trust) frameworkom (np. Hibernate Query Language (HQL)), które mogą produkować (may result) zapytania z podatnościami:

`Query HQLQuery = session.createQuery("FROM konta WHERE klientID='" + request.getParameter("id") + "'");`

W każdym z tych przypadków, atakujący zmienia wartość parametru ‘id’ w swojej przeglądarce na ' or '1'='1. Przykładowo:

`http://example.pl/app/PokazKonto?id=' or '1'='1`

Taka zmiana skutkuje tym, że zapytanie zwraca wszystkie rekordy z tabeli 'konta'. Jeszcze groźniejsze mogą być ataki, które prowadzą do modyfikacji lub usunięcia danych bądź do wywołania procedur składowanych (stored procedures).

## Odniesienia

### OWASP

* [OWASP Proactive Controls: Parameterize Queries](https://www.owasp.org/index.php/OWASP_Proactive_Controls#2:_Parameterize_Queries)
* [OWASP ASVS: V5 Input Validation and Encoding](https://www.owasp.org/index.php/ASVS_V5_Input_validation_and_output_encoding)
* [OWASP Testing Guide: SQL Injection](https://www.owasp.org/index.php/Testing_for_SQL_Injection_(OTG-INPVAL-005)), [Command Injection](https://www.owasp.org/index.php/Testing_for_Command_Injection_(OTG-INPVAL-013)), [ORM injection](https://www.owasp.org/index.php/Testing_for_ORM_Injection_(OTG-INPVAL-007))
* [OWASP Ściągawka: Injection Prevention](https://www.owasp.org/index.php/Injection_Prevention_Cheat_Sheet)
* [OWASP Ściągawka: SQL Injection Prevention](https://www.owasp.org/index.php/SQL_Injection_Prevention_Cheat_Sheet)
* [OWASP Ściągawka: Injection Prevention in Java](https://www.owasp.org/index.php/Injection_Prevention_Cheat_Sheet_in_Java)
* [OWASP Ściągawka: Query Parameterization](https://www.owasp.org/index.php/Query_Parameterization_Cheat_Sheet)
* [OWASP Automated Threats to Web Applications – OAT-014](https://www.owasp.org/index.php/OWASP_Automated_Threats_to_Web_Applications)

### Zewnętrzne

* [CWE-77: Wstrzyknięcie polecenia](https://cwe.mitre.org/data/definitions/77.html)
* [CWE-89: Wstrzyknięcie SQL](https://cwe.mitre.org/data/definitions/89.html)
* [CWE-564: Wstrzyknięcie SQL z użyciem Hibernate](https://cwe.mitre.org/data/definitions/564.html)
* [CWE-917: Wstrzyknięcie w języku Expression](https://cwe.mitre.org/data/definitions/917.html)
* [PortSwigger: Server-side template injection](https://portswigger.net/kb/issues/00101080_serversidetemplateinjection)
