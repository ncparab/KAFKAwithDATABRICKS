#######################
KAFKA WITH DATABRICKS
#######################

INTRODUCTION
-------------

This tutorial assumes you are starting fresh and have no existing Kafka or ZooKeeper data.


.. image:: kafka-databricks.png
   :width: 600px
   :height: 300px
   :alt: alternate text
   
KAFKA SETUP WITH DATABRICKS
-----------------------------

STEP 1 : Login to Databricks
===============================

:ref: https://community.cloud.databricks.com/login.html;jsessionid=webapp-shard-ce2-webapp-5c5bbd9f87-ngfbqvocwt5f40zv8o2e01k0plh7l.webapp-shard-ce2-webapp-5c5bbd9f87-ngfbq

.. image:: databrickslogin.PNG
   :width: 500px
   :height: 200px
   :alt: alternate text
   
STEP 2 : In workspace, go to user and create files
===================================================

.. image:: workspace.PNG
   :width: 400px
   :height: 200px
   :alt: alternate text
   
STEP 3 : Install Kafka 
=======================

.. image:: kafka1.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text

.. image:: kafka2.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text
   
- Download kafka using wget command

.. code-block:: bash
  
   $ wget http://mirrors.estointernet.in/apache/kafka/0.10.2.2/kafka_2.10-0.10.2.2.tgz
   
.. image:: kafka3.PNG
   :width: 800px
   :height: 400px
   :alt: alternate text
   
- Extract downloded file

.. code-block:: bash

   $ tar -xzf kafka_2.11-2.1.0.tgz
   
.. image:: kafka4.PNG
   :width: 800px
   :height: 100px
   :alt: alternate text 
   
.. image:: kafka5.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text 
   
STEP 3 : Start the server
==========================

.. code-block:: bash

   $ cd kafka_2.10-0.10.2.2
   $ ls -ltr ./
   $ bin/zookeeper-server-start.sh config/zookeeper.properties

.. image:: kafka6.PNG
   :width: 800px
   :height: 400px
   :alt: alternate text 
   
.. code-block:: bash

   $ ls -ltr
   $ cd kafka_2.10-0.10.2.2
   $ bin/kafka-server-start.sh config/server.properties
   
.. image:: kafka7.PNG
   :width: 800px
   :height: 400px
   :alt: alternate text 
   
STEP 4 : Create Topic
======================

.. code-block:: bash

   $ ls -ltr
   $ cd kafka_2.10-0.10.2.2
   $ bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
   
.. image:: kafka8.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text 

- List the topics

.. code-block:: bash

   $ ls -ltr
   $ cd kafka_2.10-0.10.2.2
   $ bin/kafka-topics.sh --list --zookeeper localhost:2181
   
.. image:: kafka9.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text 
   
STEP 5 : Start producer and send some messages to consumer
============================================================

.. code-block:: bash

   $ ls -ltr
   $ cd kafka_2.10-0.10.2.2
   $ echo "This is another message1" | bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
   
.. image:: kafka10.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text 
   
.. image:: kafka11.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text 
   
STEP 6 : Start the consumer
============================

.. code-block:: bash

   $ ls -ltr
   $ cd kafka_2.10-0.10.2.2
   $ bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
   
.. image:: kafka12.PNG
   :width: 800px
   :height: 200px
   :alt: alternate text 

