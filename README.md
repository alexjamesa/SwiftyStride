# SwiftyStride
A more concise approach to Swift's stride functions. Inspired by the simplicity of MATLAB's approach to stride, these custom operators allow for a more succinct usage of Swift's two stride functions.

######Example 1: Building `[0,2,4,6,8,10]` using `stride(through…)`

- MATLAB:       `0:2:10`
- Swift:        `0.stride(through:10, by:2)`
- SwiftyStride: `0..2..10`

######Example 2: Building `[0,2,4,6,8]` using `stride(to…)`

- Swift:        `0.stride(to:10, by:2)`
- SwiftyStride: `0..2..<10`

####Notes:
- SwiftyStride outputs an `Array<Int>`, whereas Swift outputs a `Range<Int>`  
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

print(0..2..10)
print(4..4..<16)
print(4.2..4..<16)
```
