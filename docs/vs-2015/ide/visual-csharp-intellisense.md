---
title: IntelliSense per Visual C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [J#]
- Visual C#, IntelliSense
- IntelliSense [C#]
ms.assetid: 79ca304d-dc1e-4dc9-a2a6-7808df2e588e
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ea48e1807291e935081f01e821cffafa794104f5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075759"
---
# <a name="visual-c-intellisense"></a>IntelliSense per Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense per Visual C# è disponibile durante la codifica nell'editor e durante il debug nella finestra di comando [Modalità immediata](../ide/reference/immediate-window.md).  
  
## <a name="completion-lists"></a>Elenchi di completamento  
 Gli elenchi di completamento di IntelliSense in Visual C# contengono token di Elenca membri, Completa parola e altri ancora. Forniscono funzionalità di accesso rapido a:  
  
- Membri di un tipo o spazio dei nomi  
  
- Nomi di variabili, comandi e funzioni  
  
- [Frammenti di codice](#CodeSnippets),  
  
- [Parole chiave del linguaggio](#Keywords),  
  
- [Metodi di estensione](#ExtensionMethods)  
  
  L’Elenco di completamento in C# può escludere i token irrilevanti e preselezionare quelli pertinenti al contesto. Per altre informazioni, vedere [Elenchi di completamento filtrati in C#](../misc/filtered-completion-lists-in-csharp.md) e [Elementi dell'elenco di completamento preselezionati in C#](../misc/pre-selected-completion-list-items-in-csharp.md).  
  
### <a name="CodeSnippets"></a> Frammenti di codice negli elenchi di completamento  
 In Visual C#, l'elenco di completamento include frammenti di codice che consentono di inserire facilmente corpi predefiniti di codice nel programma. I frammenti di codice vengono visualizzati nell'elenco di completamento come [Elemento Shortcut (frammenti di codice IntelliSense)](http://msdn.microsoft.com/052cc97a-5c70-42f8-b398-4c3adf670cfa) del frammento.  Per altre informazioni sui frammenti di codice disponibili per impostazione predefinita in Visual C#, vedere [Frammenti di codice Visual C#](../ide/visual-csharp-code-snippets.md).  
  
### <a name="Keywords"></a> Parole chiave del linguaggio negli elenchi di completamento  
 In Visual C#, l'elenco di completamento include anche le parole chiave del linguaggio. Per altre informazioni sulle parole chiave del linguaggio C#, vedere [Parole chiave di C#](http://msdn.microsoft.com/library/e929b0f2-4b92-4d37-8060-23d323b098ad).  
  
### <a name="ExtensionMethods"></a> Metodi di estensione negli elenchi di completamento  
 In Visual C#, l'elenco di completamento include i metodi estensione che appartengono a un ambito.  
  
> [!NOTE]
>  Nell'elenco di completamento non vengono visualizzati tutti i metodi di estensione degli oggetti <xref:System.String>.  
  
 I metodi di estensione usano un'icona diversa rispetto ai metodi di istanza. Per un elenco di icone dell’elenco, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md). Se un metodo di istanza e un metodo di estensione con lo stesso nome sono entrambi inclusi in un ambito, nell'elenco di completamento viene visualizzata l'icona del metodo di estensione.  
  
### <a name="filtered-completion-lists"></a>Elenchi di completamento filtrati  
 I membri non necessari vengono rimossi dall'elenco di completamento IntelliSense usando dei filtri.  
  
 In Visual C# vengono filtrati gli elenchi di completamento disponibili per le voci riportate di seguito:  
  
- **Interfacce e classi di base** Vengono rimosse le voci dagli elenchi di completamento IntelliSense per interfacce e classi base, sia negli elenchi di interfacce e di dichiarazioni di classe base sia negli elenchi di vincoli. Le enumerazioni, ad esempio, non vengono visualizzate nell'elenco di completamento delle classi base perché non possono essere usate per tali classi. L'elenco di completamento delle classi base contiene solo interfacce e spazi dei nomi. Se si seleziona una voce nell'elenco e si digita una virgola, IntelliSense rimuove le classi base dall'elenco di completamento perché Visual C# non supporta l'ereditarietà multipla. Lo stesso comportamento si verifica anche per le clausole di vincoli.  
  
- **Attributi**: Quando si applica un attributo a un tipo, l'elenco di completamento viene filtrato in modo da contenere solo quei tipi che discendono dagli spazi dei nomi contenenti tali tipi, ad esempio <xref:System.Attribute>.  
  
- Operatori `as` e `is`.  
  
- **Clausole catch.**  
  
- **Inizializzatori di oggetto:** Solo i membri che possono essere inizializzati verranno visualizzati nell'elenco di completamento.  
  
- **Parola chiave new**: Quando si digita `new` e poi si preme la BARRA SPAZIATRICE, viene visualizzato un elenco di completamento. In base al contesto del codice, viene selezionata automaticamente una voce nell'elenco. Per le dichiarazioni e per le istruzioni return nei metodi, ad esempio, vengono selezionate automaticamente delle voci nell'elenco di completamento.  
  
- **come gli operatori e is:** Quando si preme la BARRA SPAZIATRICE dopo aver digitato la parola chiave `as` o `is` viene visualizzato automaticamente un elenco di completamento.  
  
- Eventi: Quando si digita la parola chiave `event` l'elenco di completamento contiene solo tipi delegati.  
  
- Il parametro consente di ordinare automaticamente il primo overload di metodo corrispondente ai parametri immessi. Se sono disponibili più overload di metodi, è possibile usare le frecce verso l'alto e verso il basso per selezionare il successivo overload possibile in elenco.  
  
## <a name="most-recently-used-members"></a>Membri utilizzati più di recente  
 IntelliSense memorizza i membri recentemente selezionati nella casella popup [Elenca membri](../ide/using-intellisense.md) per il completamento del nome oggetto automatico. La volta successiva che si utilizza l'elenco dei membri, i membri utilizzati di recente vengono visualizzati nella parte superiore. La cronologia dei membri utilizzati più di recente viene cancellata tra ogni sessione nell'ambiente di sviluppo integrato.  
  
## <a name="override"></a>override  
 Quando si digita [override](http://msdn.microsoft.com/library/dd1907a8-acf8-46d3-80b9-c2ca4febada8) e si preme BARRA SPAZIATRICE, IntelliSense visualizza in una casella di riepilogo popup tutti i membri validi della classe di base di cui è possibile eseguire l'override. Digitando il tipo restituito del metodo dopo `override`, IntelliSense visualizzerà soltanto i metodi che restituiscono lo stesso tipo. Se non vengono trovate corrispondenze, IntelliSense visualizzerà tutti i membri della classe base.  
  
## <a name="automatic-code-generation"></a>Generazione automatica di codice  
  
### <a name="add-using"></a>Aggiungi using  
 L'operazione di aggiunta della direttiva using di IntelliSense consente di restare concentrati sul codice che si sta scrivendo anziché passare a un'altra parte del codice.  
  
 Per avviare l'operazione di aggiunta della direttiva using, posizionare il cursore sul riferimento a un tipo che non può essere risolto. Quando, ad esempio, si crea un'applicazione console e quindi si aggiunge `XmlTextReader` al corpo del metodo `Main`, viene visualizzato uno smart tag al di sotto dell'ultimo carattere a destra di `XmlTextReader` perché costituisce un riferimento a un tipo che non può essere risolto.  
  
 ![Aggiungi using, immagine smart tag](../ide/media/addusesmart.gif "AddUseSmart")  
  
 È quindi possibile richiamare l'operazione di aggiunta della direttiva using scegliendo tale comando dal sottomenu **Risolvi** del menu **IntelliSense** o dal menu di scelta rapida oppure richiamando l'operazione tramite lo smart tag. Lo smart tag viene visualizzato soltanto quando il cursore è posizionato in corrispondenza o in prossimità del tipo non associato.  
  
 ![Aggiungi using, immagine smart tag espansa](../ide/media/addusesmartexp.gif "AddUseSmartExp")  
  
### <a name="organize-usings"></a>Organizza using  
 L'opzione **Organizza using** consente di ordinare e rimuovere le dichiarazioni `using` e `extern` senza modificare il comportamento del codice sorgente. Nel tempo i file di origine possono diventare troppo grandi e difficili da leggere a causa di direttive `using` superflue e non organizzate. Le opzioni **Organizza using`using` compattano il codice sorgente rimuovendo le direttive**  inutilizzate e migliorano la leggibilità mettendole in ordine.  
  
 Per visualizzare le opzioni disponibili nell'ambiente di sviluppo integrato (IDE) di Visual Studio, nel menu **Modifica** scegliere **IntelliSense** e quindi selezionare **Organizza using**. IDE fornisce le seguenti opzioni per l'organizzazione e la rimozione delle direttive `usings`:  
  
### <a name="implement-interface"></a>Implementa interfaccia  
 IntelliSense offre un'opzione che consente di implementare un'[interfaccia](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) mentre si usa l'editor di codice. Per implementare correttamente un'interfaccia è in genere necessario creare una dichiarazione di metodo per ogni membro dell'interfaccia della classe. Usando IntelliSense, dopo aver digitato il nome di un'interfaccia in una dichiarazione di classe viene visualizzato uno smart tag. Lo smart tag offre la possibilità di implementare automaticamente l'interfaccia, con denominazione esplicita o implicita. Con la denominazione esplicita, le dichiarazioni di metodo contengono il nome dell'interfaccia. Con la denominazione implicita, le dichiarazioni di metodo non indicano l'interfaccia a cui appartengono. Un metodo di interfaccia con denominazione esplicita è accessibile solo tramite un'istanza di interfaccia e non tramite un'istanza di classe. Per altre informazioni, vedere [Implementazione esplicita dell'interfaccia](http://msdn.microsoft.com/library/181c901f-0d4c-4f29-97fc-895079617bf2).  
  
 Con Implementa interfaccia verrà generato il numero minimo di stub di metodo necessario per soddisfare l'interfaccia. Se una classe base implementa parti dell'interfaccia, tali stub non verranno rigenerati.  
  
### <a name="implement-abstract-base-class"></a>Implementare una classe di base astratta  
 IntelliSense offre un'opzione che consente di implementare automaticamente i membri di una classe base astratta mentre si usa l'editor di codice. Per implementare i membri di una classe base astratta è in genere necessario creare una nuova definizione di metodo per ciascun metodo della classe base astratta nella classe derivata. Usando IntelliSense, una volta digitato il nome di una classe base astratta in una dichiarazione di classe viene visualizzato uno smart tag, che offre la possibilità di implementare automaticamente i metodi della classe base. Lo smart tag offre la possibilità di implementare automaticamente i metodi della classe base.  
  
 Gli stub di metodo generati con la funzionalità di implementazione di una classe base astratta vengono modellati in base al frammento di codice definito nel file MethodStub.snippet. I frammenti di codice sono modificabili. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md).  
  
### <a name="generate-from-usage"></a>Generazione dall'utilizzo  
 La funzionalità di **generazione dall'utilizzo** consente di usare le classi e i membri prima di definirli. È possibile generare uno stub per qualsiasi classe, costruttore, metodo, proprietà, campo o enumerazione che si desidera utilizzare, ma che non è ancora stato definito. È possibile generare nuovi tipi e membri senza abbandonare la posizione corrente nel codice. Ciò riduce al minimo l'interruzione del flusso di lavoro.  
  
 Viene visualizzata una sottolineatura ondulata sotto ciascun identificatore non definito. Quando si posiziona il puntatore del mouse sull'identificatore, viene visualizzato un messaggio di errore in una descrizione comando.  
  
 Per visualizzare le opzioni appropriate, è possibile utilizzare le procedure seguenti:  
  
- Fare clic sull'identificatore non definito. Viene visualizzata una sottolineatura breve sotto il carattere più a sinistra. Posizionare il puntatore del mouse su tale breve sottolineatura. Viene visualizzato uno smart tag (un'icona). Fare clic sullo smart tag.  
  
- Fare clic sull'identificatore non definito, quindi premere CTRL+. (punto).  
  
- Fare clic con il pulsante destro del mouse sull'identificatore non definito e quindi selezionare **Genera**.  
  
  Le opzioni visualizzate possono includere quanto segue:  
  
- **Genera stub proprietà**  
  
- **Genera stub campo**  
  
- **Genera stub di metodo**  
  
- **Genera classe**  
  
- **Genera nuovo tipo** (per una classe, struct, interfaccia o enumerazione)  
  
## <a name="generate-event-handlers"></a>Genera gestori eventi  
 Nell'editor del codice, IntelliSense consente di agganciare i metodi (gestori eventi) ai campi evento.  
  
 Quando si digita l'operatore `+=` dopo un campo evento in un file con estensione cs, IntelliSense chiede di premere il tasto TAB. Questa operazione consente di inserire una nuova istanza di un delegato che punta al metodo che gestisce l'evento.  
  
 ![Associazione automatica dei pulsanti](../ide/media/vxautohookup.gif "vxAutoHookUp")  
  
 Se si preme TAB, IntelliSense termina automaticamente l'istruzione per l'utente e visualizza il riferimento al gestore eventi come testo selezionato nell'editor del codice. Per completare l'associazione automatica dell'evento, IntelliSense chiede di premere di nuovo il tasto TAB per creare uno stub vuoto per il gestore eventi.  
  
 ![Genera gestore eventi](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")  
  
> [!NOTE]
>  Se un nuovo delegato creato da IntelliSense fa riferimento a un gestore eventi esistente, IntelliSense comunica queste informazioni nella descrizione comando. È quindi possibile modificare questo riferimento. Il testo è già selezionato nell'editor del codice. In caso contrario, l'associazione automatica dell'evento è a questo punto completata.  
  
 Se si preme TAB, IntelliSense associa automaticamente un metodo con la firma corretta e posiziona il cursore nel corpo del gestore eventi.  
  
> [!NOTE]
>  Usare il comando **Posizione precedente** nel menu **Visualizza** (CTRL+-) per tornare all'istruzione di associazione dell'evento.  
  
 L'attività seguente mostra come IntelliSense aggancia automaticamente un gestore eventi denominato `button1_Click` a un campo evento denominato `button1.Click`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDE di Visual Studio](../ide/visual-studio-ide.md)
