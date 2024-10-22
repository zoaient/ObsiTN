# Exercice 1
## Q1
- Si le fork s'est fait correctement dans ce cas (on suppose que c'est le cas) pid =0 pour le fils
- Pour le père, pid != 0 donc print "Dans père x=0"
- Pour le fils pid =0 donc print "Dans fils x=2"
## Q2
### Question 1

![[Q2Q1]]
### Question 2

![[Q2Q2]]
## Question 3
### Programme 1
![[Q2Q1]]
> 4 Hello
### Programme  2
![[Q3P2]]
> 8 Hello
### Programme 3

![[Q3P3]]
> 3 Hello 
### Programme 4
![[Q3P4]]
> 1 Hello
## Question 4
### Question 1

```
int main(){
	for(int i=0; i<2; i++)
		if(fork()){
			wait(NULL)
		}
		else{
			printf(getpid(),getppid());
			exit(0);
		}
	exit(0)
}
```

### Question 2


```
int main(){
	printf(getpid(),getppid());
	for(int i=0; i<2; i++)
		if(fork()==0){
			printf(getpid(),getppid());
		}
		else{
			exit(0);
		}
	exit(0);
}
```
# Exercice 2
## Q5
```
#define N 2

int main(){
	int status, i;
	pid_t pid[N]; 
	for(i=0; i < N; i++){
		pid[i]=fork();
		if ((pid==0)){
			exit(100+i);
		}
	}
	while ((pid = waitpid(-1, &status, 0)) > 0) {
		if (WIFEXITED(status)){
			if (WEXITSTATUS(status)==0){
				printf("oui")
			}
			else{
			printf("non")
			}
		}
	if (errno != ECHILD){
		perror("erreur dans waitpid");
	}
	exit(0);
	}


}
```
### Changements
```
pid[i]=fork();
pid_t pid[N]; 

```
## Q6
