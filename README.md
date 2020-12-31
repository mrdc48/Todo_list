
### ToDo_LIST
 ``` javascript
export default class App extends React.Component{
  constructor(){
    super();
    this.state =  {
      Info: "",
      data : []
    }
  }
  Getdata = (e) => {
    this.setState({
      Info : e.target.value
    });
  }
  Addata = () =>{
    this.setState({
      data : [...this.state.data, this.state.Info]
    });
  }
  delete =(event)=>{
    var index = Number(e.target.value)
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
