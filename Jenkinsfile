
pipeline {
agent any
		stages {
		
		stage ('Jenkins-Master') {
			     agent {
		               label {
		                       label "built-in"   
		                     }     
		                } 
					steps {
							dir ("/mnt/git/"){
							           sh "git clone https://github.com/Suraj-1204/SCM.git -b master"
							           sh "cp -r EC2-Linux.pem /mnt/git/SCM"
							}
							dir ("/mnt/git/SCM"){
							           sh "scp -r -i EC2-Linux.pem indexa.html ec2-user@10.0.2.165:/var/www/html/"
							/*  }
						 
						       dir ("/mnt/git/"){
						             	sh "git clone https://github.com/Suraj-1204/SCM.git -b slave2"
						             	sh "cp -r EC2-Linux.pem /mnt/git/slave2/SCM"
							} 
							dir ("/mnt/git/slave2/SCM"){   */
							            sh "scp -r -i EC2-Linux.pem indexb.html ec2-user@10.0.3.225:/var/www/html/"
							
							}
					      }
 			    } 

			 
			 
			stage ('Slave-1') {
			     agent {
		              label {
		                      label "Slave-1"
				     /* customWorkspace "/home/ec2-user/"  */
		                    }
		                } 
					steps {
						  sh "sudo chmod -R 777 /var/www/html"
						dir("/var/www/html/") {
						        sh "sudo mv indexa.html index.html"   
							sh "sudo service httpd start"
						}
					    }
				
					
			}
			
			stage ('Slave-2'){
			     agent {
			
			           label {
				               label "Slave-2"
					  /*     customWorkspace "/home/ec2-user/"   */
			                 }
			              }
			      steps {
						  sh "sudo chmod -R 777 /var/www/html"
						dir("/var/www/html/") {
						        sh "sudo mv indexb.html index.html"   
							sh "sudo service httpd start"
						}
					    }
				
					 
				    }
		  }
	}
