- POC on distributed databases consitency with RAFT
A distributed system needs to reach a consensus on what the actual state is. etcd uses the RAFT consensus
algorithm to achieve this, which ensures that at any given moment, each node’s state is
either what the majority of the nodes agrees is the current state or is one of the previously agreed upon states. 
Understand and design a distributed consensus POC with database 
article by amazon CTO: https://www.allthingsdistributed.com/2008/12/eventually_consistent.htm




need to be market ready

performance
security
	ddos safety
	bloom filter
observability and monitorng
frontend deployment
backend deployment

devops
	segregation and pick up the relevant
	argo
	Kustomize
	helm
	scaffold
	terraform
	tecton
	jenkins
	github actions and cicd

ui 
	segregation
	https://legendary-waddle-e63250d8.pages.github.io/


backend 
	segregation
		queue
		sokets
		socket upgrade in L7 L4 loadbalancer
		grapgql
		orm
		sql
		no sql

database
	segregation
		how to choose
		optimistc vs pess
		consitency vs
		master slave
		leader election etc
grpc
design patterns
in node typescript and go
api gateway with aws/azure/gcp
cloud tech

next
react
nodejs with react
nodejs streams
nodejs child processes
tailwind
aws
serverless

system design

youloader
chatgpt summarizer extension
github  bookmark
ai projects

kubernetes
	storage class,
	policy

pki in ssh
