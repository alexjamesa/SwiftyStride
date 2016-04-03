# SwiftyStride
A more concise approach to Swift's stride functions. Inspired by the simplicity of MATLAB's approach to stride, these custom operators allow for a more succinct usage of Swift's two stride functions.

######Example 1: Building `[1,3,5,7]` using `stride(through…)`

- MATLAB:       `1:2:7`
- Swift:        `1.stride(through:7, by:2)`
- SwiftyStride: `1..2..7`

######Example 2: Building `[1,3,5]` using `stride(to…)`

- Swift:        `1.stride(to:7, by:2)`
- SwiftyStride: `1..2..<7`

######Example 3: Building `[10.0,12.5,15.0]` using `stride(through…)`

- Swift:        `10.0.stride(through:15.0, by:2.5)`
- SwiftyStride: `10.0..2.5..15.0`

####Notes:
- SwiftyStride outputs an `Array`, whereas Swift outputs a `Range`  
- Comments and suggestions welcome!

####The code:
```swift
infix operator .. {associativity left}
func .. <T where T: Strideable>(lhs: T, rhs: T) -> (T,T){
    return (lhs, rhs)
}
func .. <T where T: Strideable>(lhs: (T,T.Stride), rhs: T) -> [T]{
    return Array(lhs.0.stride(through: rhs, by: lhs.1))
}

infix operator ..< {associativity left}
func ..< <T where T: Strideable>(lhs: (T,T.Stride), rhs: T) -> [T]{
    return Array(lhs.0.stride(to: rhs, by: lhs.1))
}

print(1..2..7)
print(1..2..<7)
print(4.2..4..<16)
print(10.0..2.5..15)
print(100 .. -25 .. 10)
```
