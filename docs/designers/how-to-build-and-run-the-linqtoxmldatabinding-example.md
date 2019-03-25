---
title: "Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding"
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 846b71b768d5b1909f29c8135616714d0124193c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58069918"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Procedura: Compilare ed eseguire l'esempio LinqToXmlDataBinding

In questo argomento viene illustrato come creare e compilare il progetto LinqToXmlDataBinding di Visual Studio, nonché come eseguire il programma di esempio LinqToXmlDataBinding di WPF (Windows Presentation Foundation) risultante.

Per altre informazioni su Visual Studio, vedere [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md).

## <a name="create-the-project"></a>Creare il progetto

1. Aprire Visual Studio e creare un'**app WPF** in C# denominata **LinqToXmlDataBinding**. Il progetto dovrebbe avere come destinazione .NET Framework 3.5 (o versione successiva).

1. Se non sono già presenti, aggiungere i riferimenti di progetto per i seguenti assembly .NET:

    - System.Data

    - System.Data.DataSetExtensions

    - System.Xml

    - System.Xml.Linq

1. Compilare la soluzione premendo **CTRL**+**MAIUSC**+**B** ed eseguirla premendo **F5**. Il progetto dovrebbe essere compilato senza errori ed eseguito come applicazione WPF generica.

## <a name="add-code-to-the-project"></a>Aggiungere codice al progetto

1. In **Esplora soluzioni** rinominare il file di origine **Window1.xaml** in **L2XDBForm.xaml**. Il file di origine dipendente **Window1.xaml.cs** dovrebbe essere rinominato automaticamente in **L2XDBForm.xaml.cs**.

1. Sostituire il codice sorgente del file **L2XDBForm.xaml** con la sezione di codice illustrata nell'argomento [Codice sorgente di L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md). Usare la visualizzazione Origine per usare questo file.

1. Analogamente, sostituire il codice sorgente di **L2XDBForm.xaml.cs** con il codice disponibile in [Codice sorgente di L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).

1. Nel file **App.xaml** sostituire tutte le occorrenze della stringa `Window1.xaml` con `L2XDBForm.xaml`.

1. Premere **CTRL**+**MAIUSC**+**B** per compilare la soluzione.

## <a name="run-the-program"></a>Eseguire il programma

Il programma LinqToXmlDataBinding consente all'utente di visualizzare e modificare un elenco di libri archiviato come elemento XML incorporato.

### <a name="to-run-the-program-and-view-the-book-list"></a>Per eseguire il programma e visualizzare l'elenco di libri:

Eseguire LinqToXmlDataBinding premendo **F5** (**Avvia debug**) o **CTRL**+**F5** (**Avvia senza eseguire debug**). Viene visualizzata una finestra con il titolo **WPF Data Binding using LINQ to XML** (Data binding WPF con LINQ to XML).

- Osservare la sezione superiore dell'interfaccia utente, in cui viene visualizzato il codice **XML** non elaborato che rappresenta l'elenco di libri. Viene visualizzato tramite un controllo <xref:System.Windows.Controls.TextBlock> WPF che non consente l'interazione tramite mouse o tastiera.

- Nella seconda sezione verticale, denominata **Book List**, vengono visualizzati i libri in un elenco ordinato in testo normale. Viene usato un controllo <xref:System.Windows.Controls.ListBox> che consente la selezione tramite mouse o tastiera.

### <a name="to-add-and-delete-books-from-the-list"></a>Per aggiungere ed eliminare libri dall'elenco

- Per aggiungere un nuovo libro all'elenco, immettere i valori nei controlli **ID** e **Value**<xref:System.Windows.Controls.TextBox> (Valore) nell'ultima sezione **Add New Book** (Aggiungi nuovo libro), quindi fare clic sul pulsante **Add Book** (Aggiungi libro). Il libro viene aggiunto si all'elenco di libri che all'elenco XML. In questo programma i valori di input non vengono convalidati.

- Per eliminare un libro esistente dall'elenco, selezionarlo nella sezione **Book List** e quindi fare clic sul pulsante **Remove Selected Book**. Si noti che la voce relativa al libro è stata rimossa sia dall'elenco di libri che dal codice sorgente XML non elaborato.

### <a name="to-edit-an-existing-book-entry"></a>Per modificare una voce relativa a un libro esistente

1. Selezionare la voce del libro nella seconda sezione, **Book List**. I valori correnti dovrebbero essere visualizzati nella terza sezione, **Edit Selected Book**.

1. Modificare i valori usando la tastiera. Appena il controllo <xref:System.Windows.Controls.TextBox> perde lo stato attivo, le modifiche vengono automaticamente propagate nell'elenco di codice sorgente XML e nell'elenco di libri.

## <a name="see-also"></a>Vedere anche

- [Esempio di data binding WPF tramite LINQ to XML](../designers/wpf-data-binding-using-linq-to-xml-example.md)
- [Procedura dettagliata: esempio LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Panoramica dell'IDE di Visual Studio](../get-started/visual-studio-ide.md)