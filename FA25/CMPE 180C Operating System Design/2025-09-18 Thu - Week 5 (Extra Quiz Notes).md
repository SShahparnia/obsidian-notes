# q1
int main(){

           int r=0;

           pid_t pid = fork();

           if(pid){

                (void) waitpid(pid, &r, 0);

        } else {

                exit(-100);

       }

       printf("r=%d\n", r);

}

guessed still unsure
# q2

int main() { 

	pid_t pid= fork();
	
	if (fork()) { 
		fork(); 
	} 
	if (pid) {
		fork(); 
	} 
}

```mermaid
graph TD
    P0["P0 (original)"]
    P1["P1 (first fork child)"]

    %% First fork
    P0 --> P1

    %% Second fork from P0 and P1
    P0 --> P2["P2 (child of P0, skips body)"]
    P0 --> P3["P3 (P0's body fork)"]

    P1 --> P4["P4 (child of P1, skips body)"]
    P1 --> P5["P5 (P1's body fork)"]

    %% Final if(pid) forks only for P0-line (P0, P2, P3)
    P0 --> P8["P8 (extra fork from P0)"]
    P2 --> P6["P6 (extra fork from P2)"]
    P3 --> P7["P7 (extra fork from P3)"]

```