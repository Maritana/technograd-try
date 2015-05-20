$( document ).ready(function() {

/* ----------------------------------------
-- ИМЯ ТАБЛИЦЫ
technograd
-- ПОЛЯ БД 
id
participant
station
additional_data
----------------------------------------*/
	
  var stationsColumn = document.getElementById("showStations");
  var addPnt = document.getElementById("add");
  var table = document.getElementsByTagName("table")[0];
  var tbody = document.getElementsByTagName("tbody")[0];
  var section = document.getElementsByTagName("section")[0];
  
  var comandStations = new Object;
  comandStations.number = new Array;
  comandStations.pnt = new Array;
  comandStations.station = new Array;
  
  
  var i = 9; // 8 станций и участников есть точно
  var j = 0; // для циклов
  var k = 0;
  
  var stationsArr = [];
  var st1 = "Аэродром";
  var st2 = "Морской порт";
  var st3 = "Электро-станция";
  var st4 = "Академия наук";
  var st5 = "Транспорт";
  var st6 = "Агроферма";
  var st7 = "Космодром";
  var st8 = "Мусороперерабатывающий завод";

  stationsArr[0] = [ st1, st2 ];
  stationsArr[1] = [ st3, st4 ];
  stationsArr[2] = [ st5, st6 ];
  stationsArr[3] = [ st7, st8 ];


  addPnt.addEventListener("click", addRows);
	stationsColumn.addEventListener("click", showStations);
    
       
  function addRows(){      
    var tr = document.createElement("tr");
    var tdPnt = document.createElement("td");
    var tdStation = document.createElement("td");
    var inputPnt = document.createElement("input");
    var num = document.createElement("td");
    
    inputPnt.type = "text";
    tdStation.className = "station";
    num.innerHTML = i;
 
    tr.appendChild(num);
    tr.appendChild(tdPnt);        
    tr.appendChild(tdStation);        
    tdPnt.appendChild(inputPnt);
    tbody.appendChild(tr);      
		i++;  	   
  }
  
 
 
	function shuffle(array){
		var currentIndex = array.length, temporaryValue, randomIndex ;
		// While there remain elements to shuffle...
		while (0 !== currentIndex){
		  // Pick a remaining element...
		  randomIndex = Math.floor(Math.random() * currentIndex);
		  currentIndex -= 1;
		  // And swap it with the current element.
		  temporaryValue = array[currentIndex];
		  array[currentIndex] = array[randomIndex];
		  array[randomIndex] = temporaryValue;
		}
		return array;
	}

 
  function getStationNum(){  	
    var stations = document.getElementsByClassName("station");
    var pnt = document.getElementsByClassName("pnt");

  	shuffle(stationsArr);
 	
  	while ( j < stations.length ){	  	 	
  		if ( j % stationsArr.length == 0 ){
  			k = 0;
  	}
  		
		if ( j < stationsArr.length ){
			stations[j].innerHTML = "1) " + stationsArr[j][0] + ", 2) " + stationsArr[j][1];  
		} else {  
			stationsArr[k].reverse();
			stations[j].innerHTML = "1) " + stationsArr[k][0] + ", 2) " + stationsArr[k][1]; 
		} 	
				 					  	
		k++;	  		
	  j++;	 
	  	 		  		
  	} 	
	
	  			
  } 
  
  
  function getTableContent() {  	
		//перебор строк
		for ( j=1; j < tbody.rows.length; j++ ){
			//проверка, что не пустые
			if ( !!tbody.rows[j].cells[1].innerText ) {		
				comandStations.number[j] = tbody.rows[j].cells[0].innerText;	
				comandStations.pnt[j] = tbody.rows[j].cells[1].innerText;
				comandStations.station[j] = tbody.rows[j].cells[2].innerText;	
			}
		}

		//проверка, что все строки получили
		if ( comandStations.pnt.length == tbody.rows.length ){
			$.ajax({
				type: "POST",
				url: "postPnts.php",
				data: comandStations,
				// Выводим то что вернул PHP
				success: function(html) {
				//предварительно очищаем нужный элемент страницы
				alert("GREAT!");
				}
			});
		}
  } 
    
   
    
  function showStations() {    	
    var tdArray = document.getElementsByTagName('input');
    
    while ( j < tdArray.length ){           
      tdArray[j].parentNode.innerHTML = tdArray[j].value;           
    }
    tbody.setAttribute("id", "noI"); 
 
    getStationNum();
  	getTableContent();  	
  }
 
 
 
});