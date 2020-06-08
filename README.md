# R-programming
## Put comments here that give an overall description of what your
## functions do

##this function creates a special matrix object that can cache its inverse

makeCacheMatrix <- function(x = matrix()) {
        inv <- NULL
	set <- function(y){  ##setting value of the matrix
		x <<- y
		inv <<- NULL
	}
	get <- function() {x}
	setInverse <- function(inverse) {inv <<- inverse}
	getInverse <- function() {inv}
	list(set = set,get = get,setInverse = setInverse,getInverse = getInverse)


}


## This function computes the inverse of the special matrix returned by the above function

cacheSolve <- function(x, ...) {
        ## Return a matrix that is the inverse of 'x'
        inv <- x$getInverse() ##returns a matrix that is inverse of x
	if(!is.null(inv)){
		message("getting cache data")
		return(inv)
	}
	mat <- x$get()
	inv <- solve(mat,...) ##to compute inverse of the matrix 
	x$setInverse(inv)
	inv

}
