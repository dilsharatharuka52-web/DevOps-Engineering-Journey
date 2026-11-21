"Continuous Delivery is a software development discipline where you  build software in such a way that the software can be released to production at any time"

## Release to production at any time
- The master branch should always be ready to deploy
- You need a way to know if something will "break the build"
- Deliver every change to a production-like environment

## CI/CD pipeline
Automated gates that create a pipeline of checks:
- Unit testing
- Code quality checks
- Integration testing
- Security testing
- Vulnerability scanning
- Package signing

## A CI/CD pipeline needs
- A code repository
- A build server
- An integration server
- An artifact repository
- Automatic configuration and deployment

![[Pasted image 20261121111637.png]]

## Five key principles
 1.  Build quality in
 2.  work in small batches
 3. Computers perform repetitive tasks, people solve problems
 4. Relentlessly pursue continuous improvement
 5. Everyone is responsible
![[Pasted image 20261121112049.png]]


## How DevOps manages risk
- Deployment is king
- Deployment is decoupled from activation
- Deployment is not "one size fits all"