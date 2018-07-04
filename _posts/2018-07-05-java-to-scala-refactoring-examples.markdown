---
published: true 
---

##  Java to Scala Refactoring examples

The scala plugin in intellij provides ability to refactor java to Scala. While this is good for starters, it does break down for non-trivial cases. 

`

    @Test
    public void testMapping() {

        Map<Integer, String> oneToFive = new HashMap<>();
        for (int i = 1; i <= 5; i++) {
            String englishText = getEnglishText(i);
            oneToFive.put(i, englishText);
        }

        System.out.println(oneToFive.entrySet());

    }
`


Using the intellij scala plugin, a refactor produces this

`

      @Test def testMapping(): Unit = {
        val oneToFive = new util.HashMap[Integer, String]
        var i = 1
        while ( {  i <= 5  }) {
          val englishText = getEnglishText(i)
          oneToFive.put(i, englishText) {
            i += 1;
            i - 1
          }
        }
        System.out.println(oneToFive.entrySet)
      }

`

Not only does it not work, it is verymuch java-ish. 

`

      @Test
      def testMapping(): Unit = {
        val oneToFive: Map[Int, String] = (1 until  5).map(i => (i, getEnglishText(i))).toMap
        println(oneToFive)
      }
      
      
` 

This creates a range from 1 to 5 inclusive, then maps over each number and creates Tuple2 of (Int,String). The tuple2 is then converted to a Map.

Obviously this is contrived example. The tuple2 is sufficient if we are just printing to screen or in a context where a unique key is not needed.
