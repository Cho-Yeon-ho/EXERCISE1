1) config created
# spooldir.conf: A Spooling Directory Source

# Name the components on this agent
agent1.sources = webserver-log-source
agent1.sinks = hdfs-sink
agent1.channels = memory-channel

# Describe/configure the source
agent1.sources.webserver-log-source.type = Netcat
agent1.sources.webserver-log-source.bind = localhost
agent1.sources.webserver-log-source.port = 44444

# Describe the sink
agent1.sinks.hdfs-sink.type = logger

# Use a channel which buffers events in memory
agent1.channels.memory-channel.type = Memory
agent1.channels.memory-channel.capacity = 1000
agent1.channels.memory-channel.transactionCapacity = 100

# Bind the source and sink to the channel
agent1.sources.webserver-log-source.channels = memory-channel
agent1.sinks.hdfs-sink.channel = memory-channel

2) agent 실행
flume-ng agent \
--conf /etc/flume-ng/conf \
--conf-file $DEVSH/exercises/flume/spooldir.conf \
--name agent1 -Dflume.root.logger=INFO,console

3)  telnet  실행
telnet localhost 44444

4)  Helloworld 입력 후 결과 확인(그림파일 첨부)
