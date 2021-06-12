
### ToDo_LIST
 ``` javascript
import React from 'react';


export default class App extends React.Component{
 constructor(){
   super();
   this.state =  {
     Info: "",
     data : []
   };
 }
 Getdata = (event) => {
   this.setState({
     Info : event.target.value
   });
 }
 
 componentDidUpdate(){
 localStorage.setItem("str",JSON.stringify(this.state.data));
 }
componentDidMount (){
  let hi = JSON.parse(localStorage.getItem("str"));
  if(hi){
    this.setState({
      data : hi
    });
  }
}

 Addata = () =>{
   this.setState({
     data : [...this.state.data, this.state.Info]
     
   });
   
 };
 delete =(event)=>{
   var index = Number(event.target.value)
   var array = [...this.state.data]
   if (window.confirm("you wannna delete this")){
     array.splice(index,1)
     this.setState({
       data:array
     });
   }
 }
 render(){
   return(
     <>
      <input type="text" placeholder="enter list items" onKeyUp= {(event) =>{
      this.Getdata(event)}}/>
     <button onClick={this.Addata}> add</button>
         {this.state.data.map((item,index)=>(
       <h2 key={index}> {item}<button value={index} onClick={(event)=>{
         this.delete(event)}}> remove</button>
       } </h2>))}

     </>
  )
 }
}


```
