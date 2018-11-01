
```
import java.io.File;

public class Main {
	public static void main(String[] args) {
		File base = new File("F:\\视频\\深入理解Java虚拟机（jvm性能调优+内存模型+虚拟机原理）");
		rename(base);
		System.err.println("end");
	}

	private static void rename(File fileBase) {
		if (fileBase.isDirectory()) {
			System.err.println("进入文件夹：" + fileBase.getAbsolutePath());
			File[] files = fileBase.listFiles();
			for (File file : files) {
				rename(file);
			}
		} else {
			String fileName = fileBase.getName();
			String path = fileBase.getAbsolutePath();
			path = path.substring(0, path.lastIndexOf("\\") + 1);
			fileName = fileName.substring(fileName.lastIndexOf("】") + 1);
			fileBase.renameTo(new File(path + fileName));
			System.err.println("重命名文件为：" + path + fileName);
		}
	}
}
```
