# react-todo
reactjs的todo案例，react-cn.com/index.html

	export default class App extends Component{
	  constructor(props){
	    super(props);
	    this.state={list:[{title:"点我进入编辑模式"}],title:''};
	  }
	  addHandle(e){
	    let list = this.state.list;
	    list = list.concat([{title:this.state.title}]);
	    this.setState({list:list,title:''});
	  }
	  changeHandle(e){
	    this.setState({title:e.target.value});
	  }
	  delHandle(index){
	    console.log(index)
	    let list = this.state.list;
	    list.splice(index,1);
	    this.setState();
	  }
	  changeItem(item,e){
	    item.title = e.target.value;
	    this.setState();
	  }
	  blurHandle(item){
	    item.edit = !item.edit;
	    this.setState();
	  }
	  toEdit(item){
	    item.edit=!item.edit;
	    console.log(this.refs.txtedit)
	    this.setState();
	  }
	  render(){
	    return (
	      <div>
	        <div><input type="text" value={this.state.title} onKeyDown={(e)=>{e.keyCode==13?this.addHandle(e):undefined}} placeholder="请输入标题" onChange={this.changeHandle.bind(this)}/><button onClick={this.addHandle.bind(this)}>添加</button></div>
	        <div className="preview">{this.state.title}</div>
	        <div className="list">
	          {
	            this.state.list.map((item,index)=>{
	              return (
	                  <a key={index}>
	                    {item.edit?<input type="text" onKeyDown={(e)=>{e.keyCode==13?this.toEdit(item):undefined}} onBlur={this.blurHandle.bind(this,item)} onChange={this.changeItem.bind(this,item)} value={item.title}/>:<span onClick={this.toEdit.bind(this,item)}>{item.title}</span>}
	                    <button onClick={this.delHandle.bind(this,index)}>删除</button>
	                  </a>
	                )
	            })
	          }
	        </div>
	      </div>
	    );
	  }
	}

## 完成整个的添加编辑删除的工作