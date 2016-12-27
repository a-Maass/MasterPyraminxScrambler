<!DOCTYPE html>
<html>
<body>

<p id="kek">Random Move Master Pyraminx Scrambler! (refresh page to rescramble)</p>
<p id="scramble">k</p>
<script>
var scramble = "";
var len = 42;
var theTurns = ["U","u","R","r","L","l","B","b"];
var theSuffixes =["","'"];
/* Function by Kas Thomas, http://www.planetpdf.com/developer/article.asp?ContentID=testing_for_object_types_in_ja */
function isArray(obj){
 if(typeof obj=='object'){
  var test = obj.constructor.toString().match(/array/i); 
  return (test != null);
  }
 return false;
}
// Takes a random element of the array x.
function rndEl(x){return x[Math.floor(Math.random()*x.length)];}

function megascramble(turns, suffixes){
 var num = 1;
 var donemoves=[];
 var lastaxis;
 var i,j,k;
 for(i=0;i<num;i++){
  var s="";
  lastaxis=-1;
  for(j=0;j<len;j++){
   var done=0;
   do{
    var first=Math.floor(Math.random()*turns.length);
    var second=Math.floor(Math.random()*turns[first].length);
    if (first!=lastaxis) {
     for(k=0;k<turns[first].length;k++){donemoves[k]=0;}
     lastaxis=first;
    }
    if (donemoves[second]==0) {
     donemoves[second]=1;
     if(isArray(turns[first][second])){
      s+=rndEl(turns[first][second])+rndEl(suffixes)+" ";
     }else{
      s+=turns[first][second]+rndEl(suffixes)+" ";
     }
     done=1;
    }
   }while(done==0);
  }
  scramble = s;
  scramble += " TIPS:";
  var uTip = Math.floor(Math.random() * 3);
  if (uTip == 1) {scramble += " u"};
  if (uTip == 2) {scramble += " u'"};
  var rTip = Math.floor(Math.random() * 3);
  if (rTip == 1) {scramble += " r"};
  if (rTip == 2) {scramble += " r'"};
  var lTip = Math.floor(Math.random() * 3);
  if (lTip == 1) {scramble += " l"};
  if (lTip == 2) {scramble += " l'"};
  var bTip = Math.floor(Math.random() * 3);
  if (bTip == 1) {scramble += " b"};
  if (bTip == 2) {scramble += " b'"};
  if (uTip == 0 && rTip == 0 && lTip == 0 && bTip == 0) {scramble += " No Tips!";};
 }
}
megascramble(theTurns, theSuffixes);
document.getElementById("scramble").innerHTML = scramble;
</script> 
</body>
</html>
