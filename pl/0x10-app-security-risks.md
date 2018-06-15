# Risk - Application Security Risks

## What Are Application Security Risks?

Atakujący może użyć różnych sposobów (different paths through your application) aby zaszkodzić Twojemu biznesowi lub organizacji. Każdy z tych sposobów (paths) niesie ze sobą ryzyko, które może być na tyle istotne, że warto poświęcić mu nieco uwagi.

![App Security Risks](images/0x10-risk-1.png)

Czasami te sposoby (paths - ale tutaj to brzmi dziwnie) są bardzo łatwe do odnlezienia i wykorzystania, a czasami wyjatkowo trudne.  Podobnie spodowowana szkoda (harm) może nie mieć wpływu (no consequence) a może położyć biznes całkowicie na łopatki. Aby okresli jakie jest ryzyko dla Twojej organizacji, you can evaluate the likelihood associated with each threat agent, attack vector, and security weakness and combine it with an estimate of the technical and business impact to your organization. Together, these factors determine your overall risk.

## What's My Risk

The [OWASP Top 10](https://www.owasp.org/index.php/Top10) focuses on identifying the most serious web application security risks for a broad array of organizations. For each of these risks, we provide generic information about likelihood and technical impact using the following simple ratings scheme, which is based on the OWASP Risk Rating Methodology.  

| Threat Agents | Exploitability | Weakness Prevalence | Weakness Detectability | Technical Impacts | Business Impacts |
| -- | -- | -- | -- | -- | -- |
| Appli-   | Easy 3 | Widespread 3 | Easy 3 | Severe 3 | Business     |
| cation   | Average 2 | Common 2 | Average 2 | Moderate 2 | Specific |
| Specific | Difficult 1 | Uncommon 1 | Difficult 1 | Minor 1 |       |

W tym wydaniu zaktualizowaliśmy system oceny ryzyka (risk rating system) to assist in calculating the likelihood and impact of any given risk. For more details, please see [Note About Risks](0xc0-note-about-risks.md). 

Każda organizacja jest inna (unique) i dla każdej inne są (threat actors), cele biznesowe, oraz wpływ każdego naruszenia/ataku(breach). Dla podmiotu publicznego koszystającego z CMS (ang. content management systems) do udostępniania informacji publicznych i dla szpitala, który używa takiego samego CMS dla danych wrażliwych o stanie zdrowia (sensitive health records), the threat actors and wpływ na biznes mogą różnić się diametralnie mimo użycia tego samego oprogramowanie (can be very different for the same software). Niezmiernie wazne jest, aby rozumieć ryzyka dla organizacj (to your organization) biorąc pod uwagę (based on) applicable threat agents and (potencjalny?) wpływ na biznes.

Where possible, the names of the risks in the Top 10 are aligned with [Common Weakness Enumeration](https://cwe.mitre.org/) (CWE) weaknesses to promote generally accepted naming conventions and to reduce confusion.

## References

### OWASP

* [OWASP Risk Rating Methodology](https://www.owasp.org/index.php/OWASP_Risk_Rating_Methodology)
* [Article on Threat/Risk Modeling](https://www.owasp.org/index.php/Threat_Risk_Modeling)

### External

* [ISO 31000: Risk Management Std](https://www.iso.org/iso-31000-risk-management.html)
* [ISO 27001: ISMS](https://www.iso.org/isoiec-27001-information-security.html)
* [NIST Cyber Framework (US)](https://www.nist.gov/cyberframework)
* [ASD Strategic Mitigations (AU)](https://www.asd.gov.au/infosec/mitigationstrategies.htm)
* [NIST CVSS 3.0](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)
* [Microsoft Threat Modelling Tool](https://www.microsoft.com/en-us/download/details.aspx?id=49168)
