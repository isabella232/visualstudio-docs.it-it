---
title: "Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bebaeba2cc6f74a3ddbf059ca802252ad0bab6cf
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696151"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questo argomento viene illustrato come creare e compilare il progetto LinqToXmlDataBinding di Visual Studio, nonché come eseguire il programma di esempio LinqToXmlDataBinding di WPF (Windows Presentation Foundation) risultante.  
  
 Per altre informazioni sulla creazione di progetti tramite Visual Studio, vedere [Sviluppo di applicazioni in Visual Studio](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## <a name="creating-and-populating-the-project"></a>Creazione e popolamento del progetto  
  
#### <a name="to-create-the-starting-project"></a>Per creare il progetto iniziale  
  
1. Avviare Visual Studio e creare un'applicazione WPF in C# denominata LinqToXmlDataBinding. Per il progetto è necessario usare .NET Framework 3.5 (o versione successiva).  
  
2. Se non sono già presenti, aggiungere i riferimenti di progetto per i seguenti assembly .NET:  
  
    - System.Data  
  
    - System.Data.DataSetExtensions  
  
    - System.Xml  
  
    - System.Xml.Linq  
  
3. Compilare la soluzione premendo **CTRL+MAIUSC+B** e quindi eseguirla premendo **F5**. Il progetto dovrebbe essere compilato senza errori ed eseguito come applicazione WPF generica.  
  
#### <a name="to-add-custom-code-to-the-project"></a>Per aggiungere codice personalizzato al progetto  
  
1. In Esplora soluzioni rinominare il file di origine Window1.xaml in L2XDBForm.xaml. Il file di origine dipendente Window1.xaml.cs dovrebbe essere rinominato automaticamente in L2XDBForm.xaml.cs.  
  
2. Sostituire il codice sorgente del file L2XDBForm.xaml con la sezione di codice illustrata nell'argomento [Codice sorgente di L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). Usare la visualizzazione Origine per usare questo file.  
  
3. Analogamente, sostituire il codice sorgente di L2XDBForm.xaml.cs con il codice disponibile in [Codice sorgente di L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
4. Nel file App.xaml sostituire tutte le occorrenze della stringa "Window1.xaml" con "L2XDBForm.xaml".  
  
5. Compilare la soluzione premendo **CTRL+MAIUSC+B**.  
  
## <a name="running-the-program"></a>Esecuzione del programma  
 Il programma LinqToXmlDataBinding consente all'utente di visualizzare e modificare un elenco di libri archiviato come elemento XML incorporato.  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>Per eseguire il programma e visualizzare l'elenco di libri:  
  
1. Eseguire LinqToXmlDataBinding premendo **F5** (**Avvia debug**) o **CTRL+F5** (**Avvia senza eseguire debug**). Viene visualizzata una finestra dal titolo **Data binding WPF con LINQ to XML**.  
  
2. Osservare la sezione superiore dell'interfaccia utente, in cui viene visualizzato il codice **XML** non elaborato che rappresenta l'elenco di libri. Viene visualizzato tramite un controllo <xref:System.Windows.Controls.TextBlock> WPF che non consente l'interazione tramite mouse o tastiera.  
  
3. Nella seconda sezione verticale, denominata **Book List**, vengono visualizzati i libri in un elenco ordinato in testo normale. Viene usato un controllo <xref:System.Windows.Controls.ListBox> che consente la selezione tramite mouse o tastiera.  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>Per aggiungere ed eliminare libri dall'elenco  
  
1. Per eliminare un libro esistente dall'elenco, selezionarlo nella sezione **Book List** e quindi fare clic sul pulsante **Remove Selected Book**. Si noti che la voce relativa al libro è stata rimossa sia dall'elenco di libri che dal codice sorgente XML non elaborato.  
  
2. Per aggiungere un nuovo libro all'elenco, immettere i valori nei controlli **ID** e **Value**<xref:System.Windows.Controls.TextBox> (Valore) nell'ultima sezione **Add New Book** (Aggiungi nuovo libro), quindi fare clic sul pulsante **Add Book** (Aggiungi libro). Il libro viene aggiunto si all'elenco di libri che all'elenco XML. In questo programma i valori di input non vengono convalidati.  
  
#### <a name="to-edit-an-existing-book-entry"></a>Per modificare una voce relativa a un libro esistente  
  
1. Selezionare la voce del libro nella seconda sezione, **Book List**. I valori correnti dovrebbero essere visualizzati nella terza sezione, **Edit Selected Book**.  
  
2. Modificare i valori usando la tastiera. Appena il controllo <xref:System.Windows.Controls.TextBox> perde lo stato attivo, le modifiche vengono automaticamente propagate nell'elenco di codice sorgente XML e nell'elenco di libri.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di associazione dati di WPF con LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [Procedura dettagliata: Esempio LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Sviluppo di applicazioni in Visual Studio](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68)
