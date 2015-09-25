# r-prog-assignment2coursera
##Assignment: Caching the Inverse of a Matrix
Matrix inversion is usually a costly computation and there may be some benefit to caching the inverse of a matrix rather than compute it repeatedly (there are also alternatives to matrix inversion that we will not discuss here). The assignment is given to write a pair of functions that cache the inverse of a matrix.

Write the following functions:

makeCacheMatrix: This function creates a special "matrix" object that can cache its inverse.
cacheSolve: This function computes the inverse of the special "matrix" returned by makeCacheMatrix above. If the inverse has already been calculated (and the matrix has not changed), then the cachesolve should retrieve the inverse from the cache.
Computing the inverse of a square matrix can be done with the solve function in R. For example, if X is a square invertible matrix, then solve(X) returns its inverse.
makeCacheMatrix is a function that stores a list of functions.

makeCacheMatrix<-function(x=matrix()){
		i<-NULL
		set<-function(y) {
		x<<-y
		i<<-NULL
	}
	get<-function()x
	setinverse<-function(inverse) i<<-inverse
	getinverse<-function()i
	list(set=set,get=get,
		setinverse=setinverse,
		getinverse=getinverse)
	}

cacheSolve<-function(x,...) {
		i<-x$getinverse()
		if(!is.null(i)) {
			message("getting cached data")
			return(i)
		}
		data<-x$get()
		i<-solve(data)
		x$setinverse(i)
		i
	}		
