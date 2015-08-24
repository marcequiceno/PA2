# PA2
Solution to the Programming Assignment 2
## Caching the Inverse of a Matrix.


## This function creates a special "matrix" object that can cache its inverse.

makeCacheMatrix <- function(x = matrix()) {
 m <- NULL
 set <- function(y) {
   x <<- y
   m <<- NULL
 }
 get <- function() x
 setsolve <- function(solve) m <<- NULL
 getsolve <- function() m
 list(set=set, get=get,
      setsolve=setsolve, getsolve=getsolve)
}


## This function computes the inverse of the special "matrix" returned by makeCacheMatrix above. 


cacheSolve <- function(x, ...) {
  m <- x$getsolve()
  if(!is.null(m)) {
    message("getting cached data")
    return(m)
  }
  data <- x$get()
  m <- solve(data, ...)
  x$setsolve(m)
  m
        ## Return a matrix that is the inverse of 'x'
}
