---
title: Globalizzazione e localizzazione di Excel soluzioni
description: Informazioni sulle considerazioni speciali per Microsoft Office Excel che verranno eseguite in computer con impostazioni non in lingua inglese per Windows.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 331b68bdcf2ed65de6f60b5abb79d45e2b4a07ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139881"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalizzazione e localizzazione di Excel soluzioni
  Questa sezione contiene considerazioni speciali per le soluzioni Microsoft Office Excel eseguite in computer che hanno impostazioni di Windows non in inglese. Gli aspetti da considerare per la globalizzazione e la localizzazione di soluzioni Microsoft Office sono gli stessi implicati negli altri tipi di soluzioni create con Visual Studio. Per informazioni generali, vedere [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md).

 Per impostazione predefinita, i controlli host in Microsoft Office Excel funzionano correttamente con tutte le impostazioni internazionali di Windows, a condizione che tutti i dati passati o modificati tramite codice gestito vengano formattati usando la formattazione per la lingua inglese (Stati Uniti). Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], questo comportamento viene controllato da Common Language Runtime (CLR).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>Formattare i dati in Excel con varie impostazioni internazionali
 Tutti i dati con formattazione dipendente dalle impostazioni locali, ad esempio le date e la valuta, devono essere formattati usando il formato dati inglese (Stati Uniti) con ID delle impostazioni locali 1033 prima di essere passati a Microsoft Office Excel o prima che vengano letti dal codice del progetto di Office.

 Per impostazione predefinita, quando si sviluppa una soluzione Office in Visual Studio, il modello a oggetti di Excel si aspetta la formattazione dei dati secondo l'ID delle impostazioni locali 1033 (tale operazione viene anche definita blocco del modello a oggetti sull'ID delle impostazioni locali 1033). Questo comportamento corrisponde alla modalità di funzionamento di Visual Basic, Applications Edition. Tuttavia, questo comportamento può essere modificato nelle soluzioni Office.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Comprendere come il modello Excel a oggetti prevede sempre l'ID impostazioni locali 1033
 Per impostazione predefinita, le impostazioni locali dell'utente finale non hanno effetto sulle soluzioni Office create con Visual Studio, il cui comportamento rimane sempre quello relativo alle impostazioni locali per la lingua inglese (Stati Uniti). Ad esempio, se si ottiene o si imposta la proprietà <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> in Excel, i dati devono essere formattati nel modo previsto dall'ID delle impostazioni locali 1033. Se si usa un formato dati diverso, si potrebbero ottenere risultati imprevisti.

 Anche se si usa il formato inglese (Stati Uniti) per i dati passati o modificati da codice gestito, Excel interpreta e visualizza i dati correttamente in base alle impostazioni locali dell'utente finale. In Excel i dati vengono formattati in maniera corretta perché il codice gestito passa l'ID delle impostazioni locali 1033 insieme ai dati, a indicare che i dati sono nel formato inglese (Stati Uniti) e quindi devono essere riformattati in modo da corrispondere alle impostazioni locali dell'utente.

 Se ad esempio le opzioni internazionali degli utenti finali sono impostate sulle impostazioni locali per la lingua tedesca (Germania), ci si aspetta che la data 29 giugno 2005 sia formattata come segue: 29.06.2005. Tuttavia, se la soluzione passa la data a Excel sotto forma di stringa, è necessario formattare la data in base al formato inglese (Stati Uniti): 6/29/2005. Se la cella viene formattata come una cella di data, Excel visualizzerà la data nel formato della lingua tedesca (Germania).

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Passare altri ID delle impostazioni locali al modello Excel a oggetti
 Common Language Runtime (CLR) passa automaticamente l'ID delle impostazioni locali 1033 a tutti i metodi e le proprietà nel modello a oggetti di Excel che accettano i dati dipendenti dalle impostazioni locali. Non è possibile modificare automaticamente questo comportamento per tutte le chiamate nel modello a oggetti. Tuttavia, è possibile passare un ID delle impostazioni locali diverso a un metodo specifico usando <xref:System.Type.InvokeMember%2A> per chiamare il metodo e passando l'ID delle impostazioni locali al parametro *culture* del metodo.

## <a name="localize-document-text"></a>Localizzare il testo del documento
 I documenti, i modelli o le cartelle di lavoro contenute in un progetto includono in genere testo statico che deve essere localizzato separatamente dall'assembly e dalle altre risorse gestite. Un metodo diretto per effettuare questa operazione consiste nell'eseguire una copia del documento e tradurre il testo in Microsoft Office Word o Microsoft Office Excel. Questo processo funziona anche se non si apportano modifiche al codice, in quanto è possibile collegare un numero illimitato di documenti allo stesso assembly.

 È tuttavia necessario assicurarsi che tutte le parti del codice che interagiscono con il testo del documento continuino a corrispondere alla lingua del testo e che i segnalibri, gli intervalli denominati e gli altri campi visualizzati si adattino alle eventuali riformattazioni del documento di Office necessarie per rispettare le differenze nella grammatica e nella lunghezza del testo. Per i modelli di documenti che contengono testo relativamente breve, è possibile memorizzare il testo in file di risorse per poi caricarlo in fase di esecuzione.

### <a name="text-direction"></a>Direzione del testo
 In Excel, è possibile impostare una proprietà del foglio di lavoro per il rendering del testo da destra a sinistra. I controlli host o qualsiasi controllo con una proprietà posizionata nella finestra di progettazione corrispondono automaticamente a queste `RightToLeft` impostazioni in fase di esecuzione. Word non ha un'impostazione di documento per il testo bidirezionale (è sufficiente modificare l'allineamento del testo), quindi non è possibile eseguire il mapping dei controlli a questa impostazione. che devono quindi essere impostati individualmente. È possibile scrivere codice per esaminare tutti i controlli e imporre il rendering del testo da destra a sinistra.

### <a name="change-culture"></a>Modificare le impostazioni cultura
 Il codice di personalizzazione a livello di documento in genere condivide il thread principale dell'interfaccia utente di Excel, per cui tutte le modifiche apportate alle impostazioni cultura del thread influiscono su qualsiasi altro elemento in esecuzione su tale thread. La modifica non è limitata alla personalizzazione.

 I controlli Windows Form vengono inizializzati prima dell'avvio dei componenti aggiuntivi VSTO a livello di applicazione da parte dell'applicazione host. In queste situazioni, le impostazioni cultura devono essere modificate prima dell'impostazione dei controlli dell'interfaccia utente.

## <a name="install-the-language-packs"></a>Installare i Language Pack
 Se Windows è impostato su una lingua diversa dall'inglese, è possibile installare i Language Pack di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] in modo da visualizzare i messaggi di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nella stessa lingua di Windows. Se gli utenti finali eseguono le soluzioni con le impostazioni non in lingua inglese per Windows, devono avere il Language Pack corretto per visualizzare i messaggi di runtime nella stessa lingua di Windows. I [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Language Pack sono disponibili nell'Area download [Microsoft.](https://www.microsoft.com/download)

 Inoltre, sono necessari i Language Pack per .NET Framework ridistribuibili per i messaggi di ClickOnce. I .NET Framework Language Pack sono disponibili [nell'Area download Microsoft.](https://www.microsoft.com/download)

## <a name="regional-settings-and-excel-com-calls"></a>Impostazioni internazionali e Excel COM
 Ogni volta che un client gestito chiama un metodo su un oggetto COM e deve passare informazioni specifiche delle impostazioni cultura, usa la proprietà <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (impostazioni locali) che corrisponde alle impostazioni locali del thread corrente, che per impostazione predefinita vengono ereditate dalle impostazioni internazionali dell'utente. Tuttavia, quando si effettua una chiamata nel modello a oggetti di Excel da una soluzione Excel creata tramite gli strumenti di sviluppo di Office in Visual Studio, il formato dati inglese (Stati Uniti) con ID delle impostazioni locali 1033 viene passato automaticamente al modello a oggetti di Excel. Tutti i dati con formattazione dipendente dalle impostazioni locali, ad esempio le date e la valuta, devono essere formattati usando il formato dati inglese (Stati Uniti) prima di essere passati a Microsoft Office Excel o prima che vengano letti dal codice del progetto.

## <a name="considerations-for-storing-data"></a>Considerazioni sull'archiviazione dei dati
 Per garantire che i dati vengano interpretati e visualizzati correttamente, è necessario considerare anche i problemi che possono verificarsi quando un'applicazione archivia i dati, come le formule dei fogli di lavoro di Excel, in valori letterali stringa (hardcoded) anziché in oggetti fortemente tipizzati. È consigliabile usare i dati formattati presumendo uno stile indipendente dalle impostazioni cultura o impostato sulla lingua inglese (Stati Uniti) con ID delle impostazioni locali 1033.

### <a name="applications-that-use-string-literals"></a>Applicazioni che usano valori letterali stringa
 Tra i valori che potrebbero essere specificati a livello di codice (hardcoded) sono inclusi i valori letterali data scritti in formato inglese (Stati Uniti) e le formule dei fogli di lavoro di Excel che contengono nomi di funzioni localizzati. Un'altra possibilità potrebbe essere una stringa hardcoded contenente un numero come "1,000". In alcune impostazioni cultura questo numero viene interpretato come "mille", mentre in altre come "uno virgola zero". I calcoli e i confronti eseguiti con un formato errato possono produrre dati non corretti.

 Excel interpreta ogni stringa in base all'ID delle impostazioni locali passato con la stringa. Ciò può rappresentare un problema se il formato della stringa non corrisponde all'ID delle impostazioni locali passato. Le soluzioni Excel create tramite gli strumenti di sviluppo di Office in Visual Studio usano l'ID delle impostazioni locali 1033 (en-US) quando vengono passati tutti i dati. Excel visualizza i dati in base alle impostazioni internazionali e alla lingua dell'interfaccia utente di Excel. Visual Basic, Applications Edition (VBA) funziona allo stesso modo. Le stringhe vengono formattate come en-US e VBA passa quasi sempre 0 (valore che indica l'indipendenza dalla lingua) come LCID. Ad esempio, il codice VBA seguente visualizza un valore formattato correttamente per il 12 maggio 2004, in base alle impostazioni locali dell'utente correnti:

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 Lo stesso codice, se usato in una soluzione creata tramite gli strumenti di sviluppo di Office in Visual Studio e passato a Excel tramite l'interoperabilità COM, produce gli stessi risultati quando la data viene formattata in stile en-US.

 Esempio:

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet6":::

 Quando possibile, si consiglia di usare dati fortemente tipizzati invece di valori letterali stringa. Ad esempio, invece di archiviare una data in un valore letterale stringa, archiviarla come valore <xref:System.Double>, quindi convertirla in un oggetto <xref:System.DateTime> per la modifica.

 L'esempio di codice seguente accetta una data immessa dall'utente nella cella A5, quindi la archivia come valore <xref:System.Double>, infine la converte in un oggetto <xref:System.DateTime> per la visualizzazione nella cella A7. La cella A7 deve essere formattata per la visualizzazione della data.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet7":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet7":::

### <a name="excel-worksheet-functions"></a>Excel funzioni del foglio di lavoro
 I nomi delle funzioni dei fogli di lavoro sono tradotti internamente per la maggior parte delle versioni localizzate di Excel. Tuttavia, a causa di potenziali problemi di linguaggio e interoperabilità COM, è consigliabile usare solo nomi di funzioni in inglese nel codice.

### <a name="applications-that-use-external-data"></a>Applicazioni che usano dati esterni
 Anche il codice che apre o usa in altro modo dati esterni, ad esempio file che includono valori separati da virgole (CSV) esportati da un sistema legacy, può essere interessato se tali file vengono esportati in un altro formato diverso da en-US. L'accesso al database potrebbe non essere influenzato, in quanto si presuppone che tutti i valori siano in formato binario, a meno che il database non archivi date sotto forma di stringhe o esegua operazioni che non usano il formato binario. Inoltre, se si creano query SQL mediante i dati di Excel, a seconda della funzione usata potrebbe essere necessario verificare che siano in formato en-US.

## <a name="see-also"></a>Vedi anche

- [Procedura: Impostare come destinazione l'Office utente multilingue](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)