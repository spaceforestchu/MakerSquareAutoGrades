    function autograde (report) {
          
      var totalAverage = [];  var i, j, results = {}; 
      var totalNumberArray = report.split("\n");
    
        for(i = 0; i < totalNumberArray.length; i++){
            totalNumberArray[i] = totalNumberArray[i].split(" ");
        }
       var numbersArray = [];
       totalNumberArray.forEach(function(elements){
           numbersArray.push(elements.slice(1));
       });
       
      var mergedArray = [].concat.apply([], numbersArray);
    
      var studentScore = []; 
      for(i = 0; i < numbersArray.length; i++){
          var studentTemp = 0;
          for( j = 0; j < numbersArray[i].length; j++){
             
              studentTemp += +numbersArray[i][j];
          }
          studentScore.push(studentTemp);
      }
    
    
        var averageStudent = []; var studentTotalNum = 0;
        for(i = 0; i < numbersArray.length; i++){
             studentTotalNum =  +studentScore[i]/numbersArray[i].length;
             averageStudent.push(studentTotalNum.toFixed(1));
        }
     
    
     var totalScore = 0;
     mergedArray.reduce(function(accu, pre){
        totalScore += +pre; 
     },0); 
     
     
     
     var finalTotalAverage = totalScore/mergedArray.length;
     
     var firstNameArray = [];
     totalNumberArray.forEach(function(elements){
      var firstName = elements.shift();
          firstNameArray.push(firstName);
     });
    
    for( i = 0; i < firstNameArray.length; i++){
        results.all = +finalTotalAverage.toFixed(2);
        results[firstNameArray[i]] = +averageStudent[i];
    }
    
      return results;
    
    }
    
    autograde("Abigail 11 3 5 20 4 2 8 17 4 5\nAlexander 2 12 20 0 6 10 3 4 9 7\nAva 11 15 2 19 14 5 16 18 15 19\nEthan 6 12 0 0 5 11 0 11 12 15\nIsaBella 16 0 10 7 20 20 7 2 0 1\nJacob 2 14 17 7 1 11 16 14 14 7\nJayden 10 10 3 16 15 16 8 17 15 3\nMadison 10 11 19 4 12 15 7 4 18 13\nSophia 5 17 14 7 1 17 18 8 1 2\nWilliam 12 12 19 9 4 3 0 4 13 14");
