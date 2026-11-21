

## continuous Integration vs. Continuous Delivery
- CI/CD is not on thing
- Continuous Integration (CI) - Continuously building 
                         testing, and merging to master
- Continuous Delivery (CD)  - Continuous deploying to a production-like       environment
## Traditional development
- Developers work in long lived development branches
- Branches are periodically merged into a release
- Builds are run periodically
- Developers continue to add to the development branch
-
![[Pasted image 20261121094940.png]]

## Continuous Integration
- Developers integrate code often
- Developers work in short-lived feature branches
- Each check-in is verified by an automated build
![[Pasted image 20261121095745.png]]


## Changes are kept small
- Working in small batches
- Committing regularly
- Using pull request
- Committing all change daily

## CI automation
- Build and test  every pull request
- Use CI tools that monitor version control
- Tests should run after each build
- Never merge a pull request with failing tests

## Benefit of Continuous Integration
- Faster reaction times to changes
- Reduced code integration risk
- Higher code quality
- The code in version control works
- Master branch is always deployable


.