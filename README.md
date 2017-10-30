# Performance-Review-Systems

INSTRUCTIONS TO QUERY THE BACKEND
First user registeration
POST Request(This just stores the user in the database-userdb)
localhost:8080/user/logincreate?username=prek10&password=xye&empId=123&title=emp

Login User(this is when the user logins and gets back a list-[empId,title])
GET Request
localhost:8080/user/login?username=prek3&password=xye
On return of the title compare it with[emp/man/ceo] and display the appropriate dashboard.


Adding a new Employee-[POST]
http://localhost:8080/employee/add?empid=1600&title=L1&fullname=fayfay&teamname=team2&teammembers=mj&managername=myboss&managerpeers=mrnarcy&managerscore=5   

getting the employee/manager dashboard[GET]
http://localhost:8080/employee/getdashboard?empid=1600
Result-
{
"pscore": "1",
    
"mscore": "5",
    
"managername": "myboss",
    
"fullname": "fayfay",
    
"tscore": "6",
    
"title": "L1",
    
"teamname": "team2"
}

getting the team members name for peer review-(Employee)[GET]
http://localhost:8080/employee/getteammembers?empid=1600
Result-[
    "mj"
]

getting the questions(Employee peer eval and emp manager eval)[GET]
http://localhost:8080/review/peer 


After adding-submitting a review(employee to peer,employee to manager,manager to peer,manager to manager)[POST]
http://localhost:8080/employee/setpeerscoreobject?empid=1200&fullname=fayfay&peerscore=1&quarter=Q4

MANAGER
dashboard-same http://localhost:8080/employee/getdashboard?empid=1600[GET]
peers
to get a list of his peers-
http://localhost:8080/employee/getmanagerpeers?empid=1600[GET]
gives a list of all the peers-cards

then GET request to get questions http://localhost:8080/review/peer [GET]
and the same url to submit http://localhost:8080/employee/setpeerscoreobject?empid=1200&fullname=fayfay&peerscore=1&quarter=Q4[POST]
the same uRL from manager to his peers,manager to his manager

manager to his employees-
get the employes under him-
http://localhost:8080/employee/getteammembers?empid=1600[GET]

get the performance questions-
http://localhost:8080/review/manager [GET]

submit the review 
http://localhost:8080/employee/setmanagerscore?fullname=fayfay&managerScore=80[POST]

get the manager view of team review(Graphs)
http://localhost:8080/employee/getteamdata?teamname=team2[GET]
[
    {
 "pscore": "1",
        
"mscore": "80",
        
"fullname": "fayfay",
        
"tscore": "81"
    },
   
 {
        "pscore": "1",
        
"mscore": "5",
       
 "fullname": 
"dayday",
        
"tscore": "6"
    }
]


