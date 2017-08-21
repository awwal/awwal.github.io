---
published: true
---

## Iterator count ( Not TraversableAgain)

Got stung by a bug today. I had something similar to this. I could see the length, but the iterator never looped.

	@Test
	def iteratorTest(): Unit = {
	  val start: Int = 0
	  val step: Int = 1
	  val end: Int = 50

	  val toFifty: Iterator[Int] = Iterator.iterate(start)
		 (_.+(step)).takeWhile(_ < end)

	  println(toFifty.length)
	  toFifty.foreach(v => {
	    println(v)
	  })
	}

The debugger refused to break while I was sure it should. In cases like this I have learnt to take a deep big breadth, look away some minutes and go line by line.

Basically, the cal to .length on the iterator already moved it to the end, therefore the hasNext will return false when trying to call foreach on it.

I would expect the foreach call to throw exception if the isTraversableAgain is false ( the Iterator.iterate returns AbstractIterator with isTraversableAgain=false ) rather than silently failing.
