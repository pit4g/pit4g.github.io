---
layout: single
title: Ataque de colisión MD5
excerpt: "El algoritmo MD5 es capaz de verificar la autenticidad de un archivo o programa. En la actualidad MD5 proporciona una baja seguridad, como se describirá a continuación MD5 presenta diversos fallos."
date: 2022-02-20
classes: wide
header:
  teaser: /assets/images/htb-writeup-md5/Md5logo.png
  teaser_home_page: true
  icon: /assets/images/sec.webp
categories:
  - security
  - network
tags:  
  - md5
---

![](/assets/images/htb-writeup-md5/Md5logo.png)

El algoritmo MD5 es capaz de verificar la autenticidad de un archivo o programa. En la actualidad MD5 proporciona una baja seguridad, como se describirá a continuación MD5 presenta diversos fallos

## Archivos ejecutables con el mismo Hash

Se utiliza un programa en C que al momento de ser ejecutado rellene un vector con cierto caracter

```
#include <stdio.h>
unsigned char xyz[200] = 
{"aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"}; 
int main() { int i; for (i=0; i<200;i++){
  printf("%x", xyz[i]);
}
printf("\n");
}
```

## Website


My go-to rules is normally one of those two ruleset:

- [https://github.com/NSAKEY/nsa-rules/blob/master/_NSAKEY.v2.dive.rule](https://github.com/NSAKEY/nsa-rules/blob/master/_NSAKEY.v2.dive.rule)
- [https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule](https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule)

These will perform all sort of transformations on the wordlist and we can quickly crack the password: `PleaseSubscribe!21`


The root password from MatterMost is the same as the local root password so we can just su to root and get the system flag.

![](/assets/images/htb-writeup-delivery/root.png)

$a^2 + b^2 = c^2$
