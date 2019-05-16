---
title: Casella degli strumenti, Scheda HTML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7639225229aeaa37cd682307239d3097be313b66
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689916"
---
# <a name="toolbox-html-tab"></a>Casella degli strumenti, Scheda HTML
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La scheda **HTML** della casella degli strumenti contiene componenti utili nelle pagine Web e nei Web Form. Per visualizzare questa scheda, aprire un documento per la modifica nella finestra di progettazione HTML. Scegliere **Casella degli strumenti** dal menu **Visualizza** e quindi fare clic sulla scheda **HTML** della casella degli strumenti.  
  
 Per creare un'istanza di uno strumento nella scheda **HTML**, fare doppio clic sullo strumento per aggiungerlo al documento nel punto di inserimento corrente o selezionare lo strumento e trascinarlo nella posizione voluta nell'area di modifica.  
  
## <a name="tasks"></a>Attività  
  
- [Procedura: gestire la finestra Casella degli strumenti](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
- [Procedura: modificare le schede della Casella degli strumenti](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Elementi dell'interfaccia utente  
 Per impostazione predefinita, nella scheda HTML sono disponibili i seguenti strumenti.  
  
 **Puntatore**  
 ![Puntatore pagina HTML finestra di progettazione mobile ASP.NET](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 Questo strumento viene selezionato per impostazione predefinita quando si fa clic su una delle schede della casella degli strumenti e non è possibile eliminarlo. Il puntatore consente di trascinare oggetti nell'area di visualizzazione Progettazione, ridimensionarli e riposizionarli nella pagina o nel form. Per altre informazioni, vedere [Procedura: gestire la finestra Casella degli strumenti](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) e [Procedura: modificare le schede della Casella degli strumenti](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Input (Pulsante)**  
 ![Pulsante pagina Web HTML](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Consente di inserire un elemento `input` di `type="button"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante viene inserito `id="Button1"`, come secondo pulsante `id="Button2"` e così via.  
  
 Quando si trascina **Input (Pulsante)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputButton](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [Procedura: creare script e modificare gestori eventi](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Cenni preliminari sui controlli server Web pulsante](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> e <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Reimposta)**  
 ![Screenshot HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Consente di inserire un elemento `input` di `type="reset"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante di reimpostazione viene inserito `id="Reset1"`, come secondo `id="Reset2"` e così via.  
  
 Quando si trascina **Input (Reimposta)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputReset](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> e <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Invia)**  
 ![Screenshot HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Consente di inserire un elemento `input` di `type="submit"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante di invio viene inserito `id="Submit1"`, come secondo `id="Submit2"` e così via.  
  
 Quando si trascina **Input (Invia)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputSubmit](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> e <xref:System.Web.UI.WebControls.Button>.  
  
 **Input (Testo)**  
 ![Screenshot HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Consente di inserire un elemento `input` di `type="text"` nel documento. Per modificare il testo predefinito visualizzato, modificare l'attributo `value`. Per impostazione predefinita, come primo campo di testo viene inserito `id="Text1"`, come secondo `id="Text2"` e così via.  
  
 Quando si trascina **Input (Testo)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputText](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [Cenni preliminari sul controllo server Web TextBox](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> e <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
> È consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Convalida dell'input utente nelle pagine Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (File)**  
 ![Campo File pagina HTML](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Consente di inserire un elemento `input` di `type="file"` nel documento. Per impostazione predefinita, come primo campo file viene inserito `id="File1"`, come secondo `id="File2"` e così via.  
  
 Quando si trascina **Input (File)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputFile](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6) e <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
> È consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Convalida dell'input utente nelle pagine Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Password)**  
 ![Campo password Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Consente di inserire un elemento `input` di `type="password"`. Per impostazione predefinita, come primo campo file password viene inserito `id="Password1"`, come secondo `id="Password2"` e così via.  
  
 Quando si trascina **Input (Password)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputPassword](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Procedura: impostare un controllo server Web TextBox per l'immissione di una password](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310) e [Procedura dettagliata: convalida dell'input dell'utente in una pagina Web Form](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
> Se l'applicazione trasmette nomi utente e password, è necessario configurare il sito Web per usare SSL (Secure Sockets Layer) per la crittografia della trasmissione. Per altre informazioni, vedere "Securing Connections with SSL" (Protezione delle connessioni con SSL) in [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856) (Guida operativa di IIS). È poi consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Convalida dell'input utente nelle pagine Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Input (Casella di controllo)**  
 ![Opzione Checkbox casella degli strumenti pagina Web HTML](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Consente di inserire un elemento `input` di `type="checkbox"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come prima casella di controllo viene inserito `id="Checkbox1"`, come seconda `id="Checkbox2"` e così via.  
  
 Quando si trascina **Input (Casella di controllo)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputCheckBox](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [Cenni preliminari sul controllo server Web CheckBox e CheckBoxList](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> e <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Input (Pulsante di opzione)**  
 ![Screenshot VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Consente di inserire un elemento `input` di `type="radio"`. Per modificare il testo visualizzato, modificare la proprietà `name`. Per impostazione predefinita, come primo pulsante di opzione viene inserito `id="Radio1"`, come secondo `id="Radio2"` e così via.  
  
 Quando si trascina **Input (Pulsante di opzione)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputRadioButton](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [Cenni preliminari sul controllo server Web RadioButton e RadioButtonList](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> e <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Input (Nascosto)**  
 ![Elemento nascosto pagina HTML](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Consente di inserire un elemento `input` di `type="hidden"`. Per impostazione predefinita, come primo campo nascosto viene inserito `id="Hidden1"`, come secondo `id="Hidden2"` e così via.  
  
 Quando si trascina **Input (Nascosto)** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Per altre informazioni, vedere [Controlli Input HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Sintassi dichiarativa per il controllo server HtmlInputHidden](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9) e <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Area di testo**  
 ![Area testo casella degli strumenti pagina HTML](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Consente di inserire un elemento `textarea`. È possibile ridimensionare l'area di testo oppure usare le barre di scorrimento per visualizzare il testo che si estende oltre l'area di visualizzazione. Per modificare il testo predefinito visualizzato, modificare l'attributo `value`. Per impostazione predefinita, come prima area di testo viene inserito `id="textarea1"`, come seconda `id=" textarea 2"` e così via.  
  
 Quando si trascina **Area di testo** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Per altre informazioni, vedere [Sintassi dichiarativa per il controllo server HtmlTextArea](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> e <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
> È consigliabile convalidare tutto l'input degli utenti. Per altre informazioni, vedere [Convalida dell'input utente nelle pagine Web ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Tabella**  
 ![Screenshot HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Consente di inserire un elemento `table`.  
  
 Quando si trascina **Tabella** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Per altre informazioni, vedere [Sintassi dichiarativa per il controllo server HtmlTable](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [Cenni preliminari sui controlli server Web Table, TableRow e TableCell](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable> e <xref:System.Web.UI.WebControls.Table>.  
  
 **Immagine**  
 ![Elemento immagine pagina HTML](../../ide/reference/media/vximage.gif "vxImage")  
  
 Consente di inserire un elemento `img`. Modificare questo elemento per specificare il testo `src` e `alt`.  
  
 Quando si trascina **Immagine** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<img alt="" src="">  
```  
  
 Per altre informazioni, vedere [Sintassi dichiarativa per il controllo server HtmlImage](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [Cenni preliminari sul controllo server Web Image](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage> e <xref:System.Web.UI.WebControls.Image>.  
  
 **Seleziona**  
 ![Elenco a discesa casella degli strumenti pagina HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Consente di inserire un elemento `select` a discesa senza attributo `size`. Per impostazione predefinita, come prima casella di riepilogo viene inserito `id="select1"`, come seconda `id="select2"` e così via.  
  
 Quando si trascina **Seleziona** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 È possibile creare un elemento `select` aumentando il valore della proprietà Size.  
  
 Per altre informazioni, vedere [Sintassi dichiarativa per il controllo server HtmlSelect](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [Procedura: creare script e modificare gestori eventi](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Cenni preliminari sul controllo server Web DropDownList](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Cenni preliminari sul controllo server Web ListBox](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect> e <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Righello orizzontale**  
 ![Elemento righello orizzontale pagina HTML](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Consente di inserire un elemento `hr`. Per aumentare lo spessore della linea, modificare l'attributo `size`.  
  
 Quando si trascina **Righello orizzontale** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<hr width="100%" size=1>   
```  
  
 Per altre informazioni, vedere [Controllo Righello orizzontale HTML](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **Div**  
 ![Etichetta pagina HTML](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Consente di inserire un elemento `div` che include un attributo `ms_positioning="FlowLayout"`. Tranne che per i valori relativi a larghezza e altezza, questo elemento è identico a un pannello di layout flusso. Per formattare il testo contenuto nell'elemento `div`, aggiungere un attributo `class="stylename"` al tag di apertura.  
  
 Quando si trascina **Div** nell'area di visualizzazione Progettazione, nel documento viene inserito un markup HTML simile a quello riportato di seguito:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Per altre informazioni, vedere [Controllo Div HTML](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Cenni preliminari sul controllo server Web Label](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac) e <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>Vedere anche  
 [Casella degli strumenti](../../ide/reference/toolbox.md)   
 [Scheda Standard, Casella degli strumenti](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [Controlli HTML](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
