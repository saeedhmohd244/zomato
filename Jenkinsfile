pipeline{
	agents any

	stages{
		stage('clone the repository'){
			step{
				git branch: 'main', changelog: false, poll: false, url: 'https://github.com/saeedhmohd244/zomato.git'
			}
		}


		}
	}
}
