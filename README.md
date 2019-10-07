@[TOC](3D Game Programming & Design：游戏对象与图形基础)

# 游戏对象与图形基础
##  1、基本操作演练【建议做】
- 下载 Fantasy Skybox FREE， 构建自己的游戏场景
首先在Asset Store中搜索Fantasy Skybox FREE，点击download下载然后import导入。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005171253521.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70)
我在导入的时候遇到了一点小问题，就是点import怎么都没有反应。然后解决方法是重新启动了一次unity，然后在最上面的菜单栏找到asset->import unity package，会出现如下图所示的界面，然后导入即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005170754421.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70)
在下面asset里可以看到Fantasy Skybox FREE导入成功。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005171823140.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70)
然后我们可以在Materials里选择一个的天空盒子样式:
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005171926138.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70#pic_center =600x300)
在Assets 上下文菜单 -> create -> Material 给新建的skybox起名 mysky
在 Inspector 视图中选择 Shader -> Skybox -> 6Sided，给各个面分别贴上我们下载好的资源贴图。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005191831525.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70#pic_center =300x600)
这样一个skybox就构建好了，然后我们把它应用于当前的游戏场景中。
之后我们开始加terrain地形系统。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005192906187.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70#pic_center =200x250)
加入terrain有很多可以调的参数，如下图所示，Terrain有五个图标，左边第一个是用来增加terrain的邻居terrain的，也就是扩充地形，第二个是绘制terrain，有增加地形高低，上颜色或纹理等等功能，第三个是种树，选中树木的预制件然后在要种的地方点击即可，第四个是绘制细节，可以改笔刷的属性，最后一个是settings，就是设置整块terrain的参数的。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019100519310793.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70#pic_center =300x300)
上色后的terrain如下图所示：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005192756495.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70)
因为这个的baking过程比较长，为了节省时间，没有等整个种树效果出来就关掉了（省点电），大概游戏场景制作效果如下图所示：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191005193724969.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70)
- 写一个简单的总结，总结游戏对象的使用

GameObject 菜单上游戏元素是最基础的。尽管实际游戏生产中我们更多依赖模型、预制，但它们都是由这些元素构成。只有理解它们才能更好的控制它们。
Unity 中常用的游戏对象主要有以下几类：
>-  Empty ：不显示却是最常用对象之一，通常我们挂载脚本都是用empty对象
>作为子对象的容器
创建一个新的对象空间
>- 3D 物体：3D游戏中的重要组成部分，可以改变其网格和材质，三角网格是游戏物体表面的唯一形式。
· 基础 3D 物体（Primitive Object）：立方体（Cube）、球体（Sphere）、胶囊体（Capsule）、圆柱体（Sylinder）、平面（Plane）、四边形（Quad）
· 构造 3D 物体：由三角形网格构建的物体：如地形可用于创建陆地、山川、河流、小径等地理结构，打造用户的游戏场景。
>- 2D物体：游戏中的二维物体。
>- Camera 摄像机，观察游戏世界的窗口
>- Light 光线，游戏世界的光源，光与影是让游戏世界富有魅力。灯光是每个场景的重要组成部分。网格和纹理定义了场景的形状和外观，而灯光定义了3D环境的颜色和情绪。
>- Audio 声音：3D游戏中的声音来源。
>- UI 基于事件的 new UI 系统
>- Particle System 粒子系统与特效

## 2、编程实践

牧师与魔鬼 动作分离版

本次作业需要在上次作业的基础上，将场记中的动作分离出来，首先要创建动作管理器。
上次的牧师与恶魔中，恶魔、牧师、船这三个游戏对象，用了独立的类来实现操作，分别创建类对象后，通过用户与用户界面的交互调用不同对象的函数独立实现相对应的游戏对象的运动。而本周的动作分离版，需要用到动作管理器和动作控制器，使用动作控制器控制所有游戏对象的运动样式，而用户通过用户界面交互通知动作管理器调用传入的控制器并实现其内的游戏对象的动作。即动作分离后由管理器、控制器两个类管理动作。

动作管理是游戏内容的重要内容，这次作业要搞清楚简单动作的组合问题，实现动作管理器，实现基础动作类，回调实现动作完成通知（经典方法），其规划与设计的UML图如下所示：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191007112524527.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70)
**动作基类：**
基类创建了动作管理器的基本元素，它继承了Unity的ScriptableObject类，该类是不需要绑定GameObject对象的可编程类。其中的属性包括enable（动作是否进行），destroy（动作是否该被销毁）。同时利用接口实现游戏的通信：callback。
```javascript
public class SSAction : ScriptableObject            
	{

		public bool enable = true;                      
		public bool destroy = false;                    

		public GameObject gameobject;                   
		public Transform transform;                     
		public ISSActionCallback callback;              

		protected SSAction() {}                        

		public virtual void Start()                    
		{
			throw new System.NotImplementedException();
		}

		public virtual void Update()
		{
			throw new System.NotImplementedException();
		}
	}
```
**简单动作实现类：**
实现具体动作，将一个物体移动到目标位置，并通知任务完成。其中GetSSAction函数通过获取物体运动的目的地和速度，让unity自己建立一个动作类。当动作完成时销毁该动作并告诉管理者动作已经完成，这以功能在UpDate中实现，毕竟要通过每一帧来判断是否该结束动作。
```javascript
public class SSMoveToAction : SSAction                        //移动
	{
		public Vector3 target;        
		public float speed;           

		private SSMoveToAction(){}
		public static SSMoveToAction GetSSAction(Vector3 target, float speed) 
		{
			SSMoveToAction action = ScriptableObject.CreateInstance<SSMoveToAction>();
			action.target = target;
			action.speed = speed;
			return action;
		}

		public override void Update() 
		{
			this.transform.position = Vector3.MoveTowards(this.transform.position, target, speed*Time.deltaTime);
			if (this.transform.position == target) 
			{
				this.destroy = true;
				this.callback.SSActionEvent(this);      
			}
		}

		public override void Start() 
		{
			
		}
	}
```
**组合动作实现类：**
实现一个动作组合序列，顺序播放动作。让动作组合继承抽象动作，能够被进一步组合；实现回调接受，能接收被组合动作的事件。创建一个动作顺序执行序列，-1 表示无限循环，start 开始动作。Update方法执行执行当前动作。SSActionEvent 收到当前动作执行完成，推下一个动作，如果完成一次循环，减次数。如完成，通知该动作的管理者。Start 执行动作前，为每个动作注入当前动作游戏对象，并将自己作为动作事件的接收者。OnDestory 如果自己被注销，应该释放自己管理的动作。在UpDate中每一帧完成当前动作，当这一序列的动作完成时，停止并通过回调函数告诉管理者该序列动作已完成，并删除序列。在执行动作前，我们需要为每一个动作注入游戏对象，在Start中实现。
```javascript
public class SequenceAction: SSAction, ISSActionCallback
	{           
		public List<SSAction> sequence;    
		public int repeat = -1;           
		public int start = 0;              

		public static SequenceAction GetSSAcition(int repeat, int start, List<SSAction> sequence) 
		{
			SequenceAction action = ScriptableObject.CreateInstance<SequenceAction>();
			action.repeat = repeat;
			action.sequence = sequence;
			action.start = start;
			return action;
		}

		public override void Update() 
		{
			if (sequence.Count == 0) return;
			if (start < sequence.Count) 
			{
				sequence[start].Update();     
			}
		}

		public void SSActionEvent(SSAction source, SSActionEventType events = SSActionEventType.Competeted,  
			int intParam = 0, string strParam = null, Object objectParam = null)
		{
			source.destroy = false;          //先保留这个动作，如果是无限循环动作组合之后还需要使用
			this.start++;
			if (this.start >= sequence.Count) 
			{
				this.start = 0;
				if (repeat > 0) repeat--;
				if (repeat == 0) 
				{
					this.destroy = true;              
					this.callback.SSActionEvent(this); 
				}
			}
		}

		public override void Start() 
		{
			foreach(SSAction action in sequence) 
			{
				action.gameobject = this.gameobject;
				action.transform = this.transform;
				action.callback = this;                
				action.Start();
			}
		}

		void OnDestroy() 
		{
			
		}
	}
```
**动作管理基类：**
首先建立MonoBehavior管理动作，动作做完自动回收，在这之中必然有需要等待的动作和已经做完的动作，显然，需要等待的动作加入等待列表，需要删除的动作加入删除列表。提供了运行一个新动作的方法RunAction。该方法把游戏对象与动作绑定，并绑定该动作事件的消息接收者。
```javascript
public class SSActionManager: MonoBehaviour, ISSActionCallback                      //action管理器
	{   

		private Dictionary<int, SSAction> actions = new Dictionary<int, SSAction>();    //将执行的动作的字典集合,int为key，SSAction为value
		private List<SSAction> waitingAdd = new List<SSAction>();                       //等待去执行的动作列表
		private List<int> waitingDelete = new List<int>();                              //等待删除的动作的key                

		protected void Update() 
		{
			foreach(SSAction ac in waitingAdd)                                         
			{
				actions[ac.GetInstanceID()] = ac;                                      //获取动作实例的ID作为key
			}
			waitingAdd.Clear();

			foreach(KeyValuePair<int, SSAction> kv in actions) 
			{
				SSAction ac = kv.Value;
				if (ac.destroy) 
				{
					waitingDelete.Add(ac.GetInstanceID());
				} 
				else if (ac.enable) 
				{
					ac.Update();
				}
			}

			foreach(int key in waitingDelete) 
			{
				SSAction ac = actions[key];
				actions.Remove(key);
				DestroyObject(ac);
			}
			waitingDelete.Clear();
		}

		public void RunAction(GameObject gameobject, SSAction action, ISSActionCallback manager) 
		{
			action.gameobject = gameobject;
			action.transform = gameobject.transform;
			action.callback = manager;                                               
			waitingAdd.Add(action);                                                    
			action.Start();
		}

		public void SSActionEvent(SSAction source, SSActionEventType events = SSActionEventType.Competeted,  
			int intParam = 0, string strParam = null, Object objectParam = null)
		{
			
		}
	}		
```
**judge：**
```javascript
private int checkGameOver(){
		if (Director.cn_move == 1)
			return 0;
		int from_priest = 0;
		int from_devil = 0;
		int to_priest = 0;
		int to_devil = 0;

		int[] from_count = fromCoast.getCharacterNum ();
		from_priest = from_count [0];
		from_devil = from_count [1];

		int[] to_count = toCoast.getCharacterNum ();
		to_priest = to_count [0];
		to_devil = to_count [1];

		if (to_devil + to_priest == 6)
			return 1;//you win
		int[] boat_count = boat.getCharacterNum();
		if (boat.getTFflag () == 1) {
			from_priest += boat_count [0];
			from_devil += boat_count [1];
		} else {
			to_priest += boat_count [0];
			to_devil += boat_count [1];
		}
		if (from_priest < from_devil && from_priest > 0)
			return -1;//you lose
		if(to_priest < to_devil && to_priest > 0)
			return -1;//you lose
		return 0;//not yet finish
	}
```

**ISSActionCallback接口**
```javascript
public enum SSActionEventType : int { Started, Competeted }  

public interface ISSActionCallback  
{  
    void SSActionEvent(SSAction source, SSActionEventType events = SSActionEventType.Competeted,  
        int intParam = 0, string strParam = null, Object objectParam = null);  
} 
```

定义了事件处理接口，所有事件管理者都必须实现这个接口来实现事件调度。利用接口（ISSACtionCallback）实现消息通知，避免与动作管理者直接依赖。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191007134918208.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MDM3NzY5MQ==,size_16,color_FFFFFF,t_70)
- 最后
完整代码见GitHub，就不贴了。
[视频链接-lose🔗](https://pan.baidu.com/s/1rbntiNgW3kaTMD1t7XpCXw)
[视频链接-win🔗](https://pan.baidu.com/s/1UG4IHtZutOqjBo6Fm_zFiw)
[我的Github代码传送门](https://github.com/ZhengweiZhao/Unity3D-HW2)

