import java.io.*;
import java.net.*;
import java.awt.*;

class Download
{
	public Download()
	{
		try
		{
			for(int i = 1; i< 493;i++)
			{
				URL url = new URL("http://image.slidesharecdn.com/graphtheorynarsinghdeo-140220233341-phpapp02/95/graph-theory-narsingh-deo-" + i + "-638.jpg");
				InputStream in = new BufferedInputStream(url.openStream());
				ByteArrayOutputStream out = new ByteArrayOutputStream();
				byte[] buf = new byte[1024];
				int n = 0;
				while (-1!=(n=in.read(buf)))
				{
				   out.write(buf, 0, n);
				}
				out.close();
				in.close();
				byte[] response = out.toByteArray();
				FileOutputStream fos = new FileOutputStream("book/"+i+".jpg");
				fos.write(response);
				fos.close();
			}
		}
		catch(Exception e)
		{
			e.printStackTrace();
		}
	}
	
	public static void main(String args[])
	{
		new Download();
	}
}
