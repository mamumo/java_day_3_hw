Singleton Pattern::

The purpose of this design pattern is to ensure that a class has only the one instance.

It wants to provide a global point of access to it.

It is encapsulated with "first use initialization" or "just in time initialization"

Singletons represent anything which is unique- therefore theoretically every person is a singleton. Building on that idea... your flat has one central electrical fuse box, building has one water mains.

Singleton is known as a creational pattern- used to construct objects so that they can be decoupled from the implementing system.



When to be used?

Example:

In a system there should be only one window manager/file system. Usually singletons are used for centralized management of internal or external resources and they provide a global point of access to themselves. (Some sort of registry or a thread pool, logging is popular- one single access point to an applications log file)

Application needs one instance of an object. Also need lazy initialization and global access.


public class Singleton {

  // Private constructor prevents instantiation from other classes


  private Singleton() {}
 
  /**
   * SingletonHolder is loaded on the first execution of Singleton.getInstance() 
   * or the first access to SingletonHolder.INSTANCE, not before.
   */


  private static class SingletonHolder { 
    private static final Singleton INSTANCE = new Singleton();
  }

  public static Singleton getInstance() {
    return SingletonHolder.INSTANCE;
  }
}

Further info:

It is infamous pattern - causes a divide in the development community- some say it belongs, others say it's against object-orientation.


Negatives:

Can be used as a shortcut - not thinking properly about object visibility. 
"If you're hacking in a Singleton so that there is global access to a resource, maybe it's not the right thing to do. It might be better to work out how to pass the reference to that resource around properly."

Another area of concern is multi-threading- if two threads call the getInstance()method at the same time, you can end up with two singletons.
"Making the getInstance() method synchronised solves this issue, but then you have the performance cost - calling a synchronised version of getInstance() will be slower than the non-synchronized version."

Fun fact:

Google now provide a Singleton Detector to discourage the use of Singletons in programs.