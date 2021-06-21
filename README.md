# ChatTracker

*Code could not be posted online as this code is a solution for a class assignment.*

Project that involves processing of big data.

   Table of Contents
   -----------------

   1. Introduction 

   2. Results 

   3. What I Learned


1.) Introduction 
   --------------------------------

In this project, my professor tasked me with creating an optimal data structure that would help keep track of users and their contributions to specific chats. In this case, users and chats are just represented as input strings. The professor provided me with a set of working but extremely slow functions, and my goal was to reduce the time-complexity of these functions.

The program and set of functions run based off of an input file. The format of the input file can be seen below:

**j userName chatName**  which requests a call to join(userName, chatName)\
**t chatName**           which requests a call to terminate(chatName)\
**c userName**           which requests a call to contribute(userName)\
**l userName chatName**  which requests a call to leave(userName, chatName)\
**l userName**           which requests a call to leave(userName)

Each of the above lines corresponds to a certain member function within a class that I created. Below, you will find descriptions of what each input line does and what the corresponding member function should return:

**j userName chatName** // A user joins a chat\

The user joins a new or existing chat. Whether or not the user was associated with that chat before, that chat is now the user's current chat. If the user had previously joined that chat and not left it since then, the user's count of contributions to that chat remains the same; otherwise, it becomes 0. If the chat had previously been joined by this or any other user and has not been terminated since then, the chat's count of contributions is unchanged; otherwise, it becomes 0.

**t chatName** // A chat is terminated\

If the chat has no users associated with it or does not exist, this function returns 0; otherwise, all users associated with the chat are no longer associated with it (as if they left the chat), and the function returns the chat's count of contributions. If that chat was any user's current chat, then the existing chat the user most recently joined and hasn't left since most recenty joining becomes the user's current chat; if there is no such chat, then that user has no current chat.

  
**c userName** // A user contributes to that user's current chat\

If the user has no current chat, return 0. Otherwise, both the user's count of contributions to that user's current chat and that current chat's count of contributions are increased by one. Return the resulting user's count of contributions to that current chat.

**l userName chatName** // A user leaves a chat\

If the user is not associated with the indicated chat, return -1. Otherwise, the user is no longer associated with that chat, and the function returns the user's count of contributions to that chat. If that chat was the user's current chat, then the existing chat the user most recently joined and hasn't left since most recenty joining becomes the user's current chat; if there is no such chat, then that user has no current chat. This function leaves the chat's count of contributions unchanged.
  
**l userName** // A user leaves that user's current chat\

If the user has no current chat, return -1. Otherwise, the user is no longer associated with that user's current chat, and the function returns the user's count of contributions made to that chat. The existing chat the user most recently joined and hasn't left since most recenty joining bcomes the user's current chat; if there is no such chat, then that user has no current chat. This function leaves the chat's count of contributions unchanged.

Below is an example set of lines that could appear in a valid input file:

**j Fred Breadmaking\
j Lucy Breadmaking\
c Lucy\
c Fred\
c Fred\
l Fred Breadmaking\
t Breadmaking**

In the above example, the line **l Fred Breadmaking** should have the corresponding member function return **2**. In the line **t Breadmaking**, the corresponding member function should return **3**.

2.) Results 
   -------------------

To improve the given functions, I utilized the vector and list C++ STL's to create a hashtable that stores information regarding a user's contribution to a certain chat. The input file used to test these functions had roughly **75,000 input lines**, **1,000 chats**, and **10,000 users**. The results of my improved functions are below:

Processing Time for **Original Functions**:    **5957.48 milliseconds**  
Processing Time for **My Improved Functions**: **43.44 milliseconds**

3.) What I Learned
   ------------

During this project, I learned the importance of carefully selecting appropriate data structures to optimize one's program. After all, even if someone builds a working product, if it operates at the pace of a snail, it is not a viable solution. I learned that speed and efficiency are key components to great code. 

------------------------------------------------------------------------
Created by Nicholas P. Dean on 9/10/20.
Copyright © 2020 Nicholas P. Dean. All rights reserved. 
------------------------------------------------------------------------
