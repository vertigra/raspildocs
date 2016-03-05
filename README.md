# Вводная часть.

---

* Общая структура документации
 * [Raspil. Разработка](raspil/raspil_dev.md)
 * [Raspil. Использование](raspil/raspil_used.md)
 * [Cупер Окна. Разработка.](sw/sw_dev.md)
 * [Супер Окна. Использование.](sw/sw_used.md)

---

 Сопутствующие проекты:

* PrintFill - автоматизация на рабочих местах.
* BarcodeRegister - сканер штрих-кода Casio.
* Pila - автоматизация двухголовой усорезной пилы.
* SpsExchangeServer - сервер и клиент синхронизации данных для автоматической оправки стеклопакетов.
* PaperlessWorkstation - следующее поколение программы Raspil.
* CatFabClient - автоматизация рабочего места обрабатывающего центра CatFab.

---

{%ace edit=true, lang='csharp'%}

// test syntax higlayting

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
```

