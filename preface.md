# Preface

OpenVPN is an outstanding piece of software that was invented by James Yonan
in the year 2001 and has steadily been improved since then. No other VPN solution
offers a comparable mixture of enterprise-level security, usability, and feature
richness. We have been working with OpenVPN for many years now, and it has
always proven to be the best solution. This book is intended to introduce OpenVPN
software to network specialists and VPN newbies alike. OpenVPN works where
most other solutions fail and exists on almost any platform. Thus, it is an ideal
solution for problematic setups and an easy approach for the inexperienced.
On the other hand, the complexity of classic VPN solutions, especially IPsec, gives
the impression that VPN technology in general is diffcult and a topic only for very
experienced (network and security) specialists. OpenVPN proves that this can be
different, and this book aims to document that.
I want to provide both a concise description of OpenVPN's features and an
easy-to-understand introduction for the inexperienced. Though there may be many
other possible ways to success in the scenarios described, the ones presented have
been tested in many setups and have been selected for simplicity reasons.

## What this book covers

Chapter 1, VPN—Virtual Private Network, gives a brief overview about what VPNs
are, what security means here, and similar important basics.

Chapter 2, VPN Security, introduces basic security concepts necessary to understand
VPNs and OpenVPN in particular. We will have a look at encryption matters,
symmetric and asymmetric keying, and certifcates.

Chapter 3, OpenVPN, discusses OpenVPN, its development, features, resources,
advantages, and disadvantages compared to other VPN solutions, especially IPsec.

Chapter 4, Installing OpenVPN on Windows and Mac, shows step-by-step how to
install OpenVPN on clients using Apple or Microsoft products.

Chapter 5, Installing OpenVPN on Linux and Unix Systems, deals with simple
installation on Linux and Unix.

Chapter 6, Advanced OpenVPN Installation, shows you how to get OpenVPN up and
running even when it gets diffcult or non-standard.

Chapter 7, Confguring an OpenVPN Server—The First Tunnel, introduces the use of
OpenVPN to build a frst tunnel.

Chapter 8, Setting Up OpenVPN with X.509 Certifcates, explains us how to use
OpenVPN to build a tunnel using the safe and easily manageable certifcates.

Chapter 9, The Command openvpn and Its Confguration File, groups an abundance of
command-line options that OpenVPN has to offer into several tables, which enable
you to search and fnd the relevant once far more easily.

Chapter 10, Securing OpenVPN Tunnels and Servers, shows how to use several
Firewalls (Windows and Linux) and security-relevant extensions like Authentication
for OpenVPN.

Chapter 11, Advanced Certifcate Management, deals with security issues, and
advanced certifcate management tools, such as TinyCA or xca, help us understand
and manage a PKI thoroughly.

Chapter 12, OpenVPN GUI Tools, shows you how to choose a suitable client out of
three GUI-tools for OpenVPN for your setup.

Chapter 13, Advanced OpenVPN Confguration, discusses tunneling proxies, pushing
confgurations from the server to the client, and many other examples up to clusters
and redundancy.

Chapter 14, Mobile Security with OpenVPN, teaches us how to connect our mobile
device, be it Windows Mobile, an embedded Linux device, or a laptop, to our VPN
and start communicating privately.

Chapter 15, Troubleshooting and Monitoring, will help you in many cases when you
run into network problems, or if anything doesn't work.
Appendix, Internet Resources and More, holds all abbreviations used and all weblinks
found throughout the whole book.

## What you need for this book
For learning VPN technologies, it may be helpful to have at least two or four PCs.
Virtualization tools like KVM, XEN, or VMware are very helpful here, especially
if you want to test with different operating systems and switch between varying
confgurations easily. However, one PC is completely enough to follow the course of
this book.
Two separate networks (connected by the Internet) can provide a useful setup if you
want to test frewall and advanced OpenVPN setup.

## Who this book is for

This book is for Newbies and Admins alike. Anybody interested in security and
privacy in the internet, and anybody who wants to have his or her notebook or
mobile phone connect safely to the Internet will learn how to connect to and how
to set up the server in the main branch of his or her company or at home. You will
learn how to build your own VPN, surf anonymously and without censorship,
connect branches over the Internet in a safe way, and learn all the basics on how to
administer and build Virtual Private Networks.

## Conventions

In this book, you will fnd a number of styles of text that distinguish between
different kinds of information. Here are some examples of these styles, and an
explanation of their meaning.
Code words in text are shown as follows: "We can include other contexts through the
use of the include directive."
A block of code will be set as follows:

remote xxx.dyndns.org
(...)
tls-remote "/C=DE/ST=BY/O=Feilner-IT/CN=VPN-Server/
emailAddress=security@feilner-it.net"
(...)
resolv-retry 86400

When we wish to draw your attention to a particular part of a code block, the
relevant lines or items will be shown in bold:
suse01:/var/log # ldapwhoami -x -h 10.10.10.1 -D
uid=mfeilner,ou=Feilner-it_Users,dc=feilner-it,dc=home -w correct_
password
dn:uid=mfeilner,ou=Feilner-it_Users,dc=feilner-it,dc=home
suse01: # ldapwhoami -x -h 10.10.10.1 -D uid=mfeilner,ou=Feilner-it_
Users,dc=feilner-it,dc=home -w wrong_password
ldap_bind: Invalid credentials (49)
Any command-line input or output is written as follows:
opensuse01:~ # echo "1" > /proc/sys/net/ipv4/ip_forward
opensuse01:~ #
New terms and important words are shown in bold. Words that you see on the
screen, in menus or dialog boxes for example, appear in our text like this: "Start YaST
on your SuSE Linux system and change to the Firewall module, which can be found
in Security and Users".
Warnings or important notes appear in a box like this.
Tips and tricks appear like this.

## Reader feedback

Feedback from our readers is always welcome. Let us know what you think about
this book—what you liked or may have disliked. Reader feedback is important
for us to develop titles that you really get the most out of.
To send us general feedback, simply drop an email to feedback@packtpub.com,
and mention the book title in the subject of your message.
If there is a book that you need and would like to see us publish, please send
us a note in the SUGGEST A TITLE form on www.packtpub.com or email
suggest@packtpub.com.
If there is a topic that you have expertise in and you are interested in either writing
or contributing to a book, see our author guide on www.packtpub.com/authors.

## Customer support

Now that you are the proud owner of a Packt book, we have a number of things to
help you to get the most from your purchase.

## Errata

Although we have taken every care to ensure the accuracy of our contents, mistakes
do happen. If you fnd a mistake in one of our books—maybe a mistake in text or
code—we would be grateful if you would report this to us. By doing so, you can save
other readers from frustration, and help us to improve subsequent versions of this
book. If you fnd any errata, please report them by visiting http://www.packtpub.
com/support, selecting your book, clicking on the let us know link, and entering
the details of your errata. Once your errata are verifed, your submission will be
accepted and the errata added to any list of existing errata. Any existing errata can be
viewed by selecting your title from http://www.packtpub.com/support.

## Piracy

Piracy of copyright material on the Internet is an ongoing problem across all media.
At Packt, we take the protection of our copyright and licenses very seriously. If
you come across any illegal copies of our works in any form on the Internet, please
provide us with the location address or web site name immediately so that we can
pursue a remedy.
Please contact us at copyright@packtpub.com with a link to the suspected
pirated material.
We appreciate your help in protecting our authors, and our ability to bring you
valuable content.

## Questions

You can contact us at questions@packtpub.com if you are having a problem with
any aspect of the book, and we will do our best to address it.
