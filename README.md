# HITDAY27

package hit.day27;
public class GenericsDemo {
	public static void main(String[] args) {
		Paint paint=new RedPaint();
		GoodPaintBrush brush=new GoodPaintBrush();
		
		brush.paint=paint;
		
		brush.doPaint();
		
		BadPaintBrush bpb=new BadPaintBrush();
		bpb.doPaint(1);
	}
}
abstract class Paint{
	
}
class RedPaint extends Paint{
	
}
class BluePaint extends Paint{
	
}
class GoodPaintBrush{
	Paint paint;
	public void doPaint() {
		System.out.println(paint);
	}
}
class BadPaintBrush{
	public void doPaint(int i) {
		if(i==1) {
			RedPaint rp=new RedPaint();
			System.out.println("red paint...."+rp);
		}
		else if(i==2) {
			BluePaint bp=new BluePaint();
			System.out.println("blue paint...:"+bp);
		}
	}
}


package hit.day27;
public class GenericsDemo {
	public static void main(String[] args) {
		Paint paint=new RedPaint();
		
		Powder powder=new RosePowder();
		
		GoodPaintBrush brush=new GoodPaintBrush();
		
		brush.obj=powder;
		
		brush.execute();
		
		
	}
}
abstract class Paint{
	public abstract void color();
}
class RedPaint extends Paint{
	@Override
	public void color() {
		System.out.println("red colour...");
	}
}
class BluePaint extends Paint{
	@Override
	public void color() {
		System.out.println("blue colour...");
	}
}
abstract class Powder{
	public abstract void doMakeup();
}
class WhitePowder extends Powder{
	@Override
	public void doMakeup() {
		System.out.println("applying powder....");
	}
}
class RosePowder extends Powder{
	@Override
	public void doMakeup() {
		System.out.println("rose powder applied..");
	}
}
class GoodPaintBrush{// I have made my paintbrush generic
	Object obj; // by declaring a object reference u can consume any object
	public void execute() {
		if(obj instanceof Paint) {
			Paint paint=(Paint)obj;
			paint.color();
		}
		if(obj instanceof Powder) {
			Powder makeup=(Powder)obj;
			makeup.doMakeup();
		}
	}
	
}
class BadPaintBrush2{// this paintbrush was specific
	Paint paint; // by declaring a specific type, you can consume only an object of that type - because java is a strongly typed language...
	public void doPaint() {
		System.out.println(paint);
	}
}
class BadPaintBrush{
	public void doPaint(int i) {
		if(i==1) {
			RedPaint rp=new RedPaint();
			System.out.println("red paint...."+rp);
		}
		else if(i==2) {
			BluePaint bp=new BluePaint();
			System.out.println("blue paint...:"+bp);
		}
	}
}


package hit.day27;
public class BasicGenerics {
	public static void main(String[] args) {
		Ball obj=new Ball();
		Sky sky=new Sky();
		
		//Accept accept=new Accept();
		//accept.obj=sky;
		
		//accept.process();
		
		RightAccept<Ball> raccept=new RightAccept<>();
		raccept.setT(sky);
		
		RightAccept<Sky> raccept2=new RightAccept<>();
		raccept2.setT(sky);
		
		Ball ball=raccept.getT();
		
		Sky s=raccept2.getT();
		
	}
}
class Sky{
	
}
class Ball{
	
}
class RightAccept<T>{
	T obj;
	public T getT() {
		return obj;
	}
	public void setT(Sky sky) {
		this.obj=(T) sky;
	}
}
class Accept{
	Object obj;
	public void process() {
		if(obj instanceof Ball) {
			Ball ball=(Ball)obj;
			System.out.println(ball);
		}
		else if(obj instanceof Sky) {
			Sky sky=(Sky)obj;
			System.out.println(sky);
		}
	}
}
  
  
  package hit.day27;
import java.util.ArrayList;
import java.util.List;
public class GenericsInCollection {
	public static void main(String[] args) {
		List<String> list=new ArrayList<>();// you are using generic collection of jdk 1.5 to make it specific
		
		list.add("aaaa");
		list.add("bbbb");
		list.add("fdsafdsa");
		
		//process this collection...
		
		//String s=(String)list.get(1);
		//Box s2=(Box)list.get(2);
		
//		for(Object ob:list) {
//			if(ob instanceof String) {
//				String ss=(String)ob;
//				System.out.println(ss);
//			}
//			else if(ob instanceof Box) {
//				Box bb=(Box)ob;
//				System.out.println(bb);
//			}
//		}
		for(Object ob:list) {
			String s=(String)ob;
			System.out.println(s);
		}
	}
}
class Box{
	
}
  
  
  package hit.day27;
public class GenericsDemo {
	public static void main(String[] args) {
		Paint paint=new RedPaint();
		
		Powder powder=new RosePowder();
		
		GoodPaintBrush<Paint> brush=new GoodPaintBrush<>();
		
		brush.setObj(paint);
		
		Paint mypaint=brush.getObj();
		mypaint.color();
		
		GoodPaintBrush<Powder> brush2=new GoodPaintBrush<>();
		brush2.setObj(new RosePowder());
		
		Powder myPowder=brush2.getObj();
		myPowder.doMakeup();
		
		
	}
}
abstract class Paint{
	public abstract void color();
}
class RedPaint extends Paint{
	@Override
	public void color() {
		System.out.println("red colour...");
	}
}
class BluePaint extends Paint{
	@Override
	public void color() {
		System.out.println("blue colour...");
	}
}
abstract class Powder{
	public abstract void doMakeup();
}
class WhitePowder extends Powder{
	@Override
	public void doMakeup() {
		System.out.println("applying powder....");
	}
}
class RosePowder extends Powder{
	@Override
	public void doMakeup() {
		System.out.println("rose powder applied..");
	}
}
class GoodPaintBrush<T>{
	T obj;
	public void setObj(T obj) {
		this.obj=obj;
	}
	public T getObj() {
		return this.obj;
	}
}
class BadPaintBrush3{// I have made my paintbrush generic
	Object obj; // by declaring a object reference u can consume any object
	public void execute() {
		if(obj instanceof Paint) {
			Paint paint=(Paint)obj;
			paint.color();
		}
		if(obj instanceof Powder) {
			Powder makeup=(Powder)obj;
			makeup.doMakeup();
		}
	}
	
}
class BadPaintBrush2{// this paintbrush was specific
	Paint paint; // by declaring a specific type, you can consume only an object of that type - because java is a strongly typed language...
	public void doPaint() {
		System.out.println(paint);
	}
}
class BadPaintBrush{
	public void doPaint(int i) {
		if(i==1) {
			RedPaint rp=new RedPaint();
			System.out.println("red paint...."+rp);
		}
		else if(i==2) {
			BluePaint bp=new BluePaint();
			System.out.println("blue paint...:"+bp);
		}
	}
}
  
  package hit.day27;
public class BasicGenerics {
	public static void main(String[] args) {
		Ball obj=new Ball();
		Sky sky=new Sky();
		
		//Accept accept=new Accept();
		//accept.obj=sky;
		
		//accept.process();
		
		RightAccept<Ball> raccept=new RightAccept<>();
		raccept.setT(obj);
		
		RightAccept<Sky> raccept2=new RightAccept<>();
		raccept2.setT(sky);
		
		Ball ball=raccept.getT();
		
		Sky s=raccept2.getT();
		
	}
}
class Sky{
	
}
class Ball{
	
}
class RightAccept<T>{
	T obj;
	public T getT() {
		return obj;
	}
	public void setT(T obj) {
		this.obj=obj;
	}
}
class Accept{
	Object obj;
	public void process() {
		if(obj instanceof Ball) {
			Ball ball=(Ball)obj;
			System.out.println(ball);
		}
		else if(obj instanceof Sky) {
			Sky sky=(Sky)obj;
			System.out.println(sky);
		}
	}
}
  
  
