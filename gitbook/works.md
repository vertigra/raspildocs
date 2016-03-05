# GitBook. Приемы работы.


---


### Подсветка кода
Для подсветки кода используется плагин [GitBook Ace Plugin.](https://plugins.gitbook.com/plugin/ace) 
Базовый синтаксис который следует использовать для подсветки кода:

```
{%ace edit=true, lang='c_cpp'%}
// This is a hello world program for C.
#include <stdio.h>

int main(){
  printf("Hello World!");
  return 1;
}
{%endace%}
```
Из описания к плагину.

edit: if this is set to true, the code will be editable by the user.

lang: the language for syntax highlight. For the full list of keyword for each language, please check out the [github page](https://github.com/ajaxorg/ace-builds/tree/master/src-min-noconflict) of ace here, all the related files are starting with prefix mode-. For instance:
        * mode_c_cpp.js ----> c_cpp
        * mode_java.js ----> java
        ...
check: if this is set to false, syntax validation will be disabled.

theme: the theme for the editor, the default is 'chrome'.
        * monokai
        * coffee
        * ...

Пример работы.

{%ace edit=false, lang='csharp', check=true, theme='monokai'%}

// подсветка кода C#
// параметры редактора
// {%ace edit=false, lang='csharp', check=true, theme='monokai'%}

  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
    }
    private void button1_Click(object sender, EventArgs e)
    {
      PilaDLL.SendData(Properties.Settings.Default.PilaPort, Convert.ToDouble(textBox1.Text), 100, 100);
    }

    private void button3_Click(object sender, EventArgs e)
    {
      PilaDLL.TestDLL(Properties.Settings.Default.PilaPort, Convert.ToDouble(textBox1.Text), 100, 100);
    }

    private void button2_Click(object sender, EventArgs e)
    {
      Close();
    }

    
    private void button5_Click(object sender, EventArgs e)
    {
      int i = Convert.ToInt32(textBox2.Text);
      textBox2.Text = (++i).ToString();
    }

    private void button4_Click(object sender, EventArgs e)
    {
      button5_Click(this, null);
      string data = richTextBox1.Text.Replace("__NUM__", textBox2.Text);
      DataSets.ComPrinter cp = new DataSets.ComPrinter(Properties.Settings.Default.PrinterPort);
      cp.sendData(data);
      cp.closePort();
    }

  }

{%endace%}




