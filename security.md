# Software Security

**Course Outcome 5**	Develop a security mindset that anticipates adversarial exploits in software architecture and designs to expose potential vulnerabilities, mitigate design flaws, and ensure privacy and enhanced security of data and resources.

In my studies, I have strengthened my security mindset that anticipates software exploits and designs to mitigate them. CS305, Software Security, helped me to anticipate a wide range of vulnerabilities that emerge when we work with code. According to Detlefsen & Maniaco, following a deny-by-default policy can ensure that fewer vulnerabilities and opportunities for potential exploits will be missed (2015). This is also referred to as the principle of least privilege, in which users should be given the minimum levels of access and permissions necessary to perform essential tasks. I agree with this approach and regularly practice a deny-by-default practice to software development that can avoid many serious repercussions. 

In CS305, I learned that using the National Vulnerability Database (NVD) as a resource to guide risk assessment when including third party libraries, ensuring secure HTTPS protocols, and implementing robust security configurations (for example: Spring Security) are some ways that we can ensure the security of our applications. To meet the needs of a financial industry consulting firm seeking to enhance the security of its web application, I implemented a robust hashing algorithm to protect sensitive client communications, I recommended encryption and cloud backup practices to ensure data security, and I migrated the HTTP site to a secure HTTPS certificate-requiring site. To protect against SQL injection, I recommended implementing strong input validation prohibiting characters such as * , < , > , or /.  In this class, I also became practiced at generating, trusting, and revoking trust for certificates. 

-**My work in this project demonstrated proficiency in developing a security mindset that anticipates exploits in software architecture and designs to expose potential vulnerabilities with skills in Java, software testing, software security, Spring Security, Windows, and Eclipse.** You can see an example of a dependency check maven report that I created to assess software vulnerabilities associated with third-party packages [using the National Vulnerability Database here](https://sheraadams.github.io/CS305). You can also see that **I reduced the overall number of vulnerabilities from 118 to 70** by updating dependencies to their newest versions and suppressing some low-severity vulnerabilities that would not be expected to impact the project significantly.