## Stone Paper Scissors Solution### Stone```Stone >> play: anotherTool
	^ anotherTool playAgainstStone: self``````Paper >> playAgainstStone: aStone
	^ #paper``````Scissors >> playAgainstStone: aStone
	^ #stone``````Stone >> playAgainstStone: aStone
	^ #draw```### Scissors```Scissors >> playAgainstScissors: aScissors
	^ #draw``````Paper >> playAgainstScissors: aScissors
	^ #scissors``````Stone >> playAgainstScissors: aScissors
	^ #stone``````Scissors >> play: anotherTool
	^ anotherTool playAgainstScissors: self```### Paper```Scissors >> playAgainstPaper: aPaper
	^ #scissors``````Paper >> playAgainstPaper: aPaper
	^ #draw``````Stone >> playAgainstPaper: aPaper
	^ #paper``````Paper >> play: anotherTool
	^ anotherTool playAgainstPaper: self```