####Start rabbitmq server:

`````bash
$ sudo rabbitmq-server
`````

####Start one worker:

`````bash
$ ./manage.py celery worker --config=calculon/settings -E -l debug
`````

####Start multiple workers:

Starting two workers(image and video) but this workers should process any task(not assinged to the any specific queue).

`````bash
$ ./manage.py celeryd_multi start image video --config=calculon/settings -E -l debug 
`````

####Assigning workers to queues:

Assigned queue not process the another tasks, process only tasks which specified with the queue kwarg.

`````bash
$ ./manage.py celeryd_multi start image --config=calculon/settings -Q image_resizing  -E -l debug
`````

`````python
my_task.apply_async(params, queue='image_resizing')
`````

####Periodic Tasks

Start celery beat:
`````bash
$ ./manage.py celerybeat
`````

Embed beat inside to the worker
`````bash
$ ./manage.py worker -B
`````


##Celery 

Process task on any worker because queue not specified
`````python
MyTask.delay(*args)
`````

Send task to specific queue(We can assign workers to queues but worker must be started with `-Q my_queue` arguments )
`````python
MyTask.apply_async(args, queue="my_queue")
`````


####Helper tools:

- celery flower
- rabbitmq management plugin
