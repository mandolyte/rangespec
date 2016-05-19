# rangespec
Parsing a Range Specification, such as, "1,3,5-8,12-"

A number of checks are made to ensure that range is well formed.
- an open ended range must be the last one
- the start must be equal or greater than stop of an element
- the start of an element must be greater than stop of prior element
- no element may be zero (range begins at one)

Usage:

```
package main

import "github.com/mandolyte/rangespec"
import "log"
import "fmt"

func main() {
  input := "1,3,5-8,12-"
  fmt.Printf("Input is %v\n",input)
  result,err := rangespec.RangeSlice(input)
  if err != nil {
    // handle error
    log.Fatalf("Error:%v",err)
  }
  for n := range result {
    start := result[n].Start
    stop := result[n].Stop
    fmt.Printf("Start %v, Stop %v\n",start,stop)
  }
  // or
  for _, val := range result {
    start := val.Start
    stop := val.Stop
    fmt.Printf("Start %v, Stop %v\n",start,stop)
  }
}
```
