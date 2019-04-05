---
title: Debug di progetti DLL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 365a53edf79e301d89d9060d225525b713171158
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968341"
---
# <a name="debugging-dll-projects"></a>Debug di progetti di DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Di seguito sono elencati i modelli per la creazione di DLL:  
  
- (C++, C# e Visual Basic): Libreria di classi  
  
- (C++, C#e Visual Basic): Libreria di controllo Windows Form  
  
   Il debug di una libreria di controlli Windows è simile al debug di un progetto Libreria di classi. Nella maggior parte dei casi si effettua una chiamata al controllo Windows da un altro progetto. Quando si esegue il debug del progetto chiamante, è possibile eseguire l'istruzione del codice del controllo Windows, impostare i punti di interruzione ed eseguire altre operazioni di debug. Per altre informazioni, vedere [Controlli Windows Form](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a).  
  
- (C# e Visual Basic): Libreria di controlli Web  
  
   Per altre informazioni, vedere [Web Control Library (Managed Code)](../debugger/web-control-library-managed-code.md).  
  
- (C++): Controllo ActiveX MFC e controllo ActiveX MFC per Smart Device  
  
   I controlli ActiveX sono controlli che possono essere scaricati attraverso Internet in un computer client, nonché visualizzati e attivati in pagine Web.  
  
   Il debug dei controlli ActiveX è simile a quello di altri tipi di controlli poiché non possono essere eseguiti in modalità autonoma, ma devono essere incorporati in una pagina Web HTML. Per altre informazioni, vedere [Procedura: Eseguire il debug di un controllo ActiveX](../debugger/how-to-debug-an-activex-control.md).  
  
- (C++): MFC per Smart Device DLL  
  
   Per altre informazioni, vedere [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md).  
  
  In questa sezione vengono inoltre trattati i seguenti argomenti:  
  
- [Procedura: Eseguire il debug da un progetto DLL](../debugger/how-to-debug-from-a-dll-project.md)  
  
- [Procedura: Eseguire il debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md)  
  
  In questo argomento sono contenute le seguenti sezioni relative alla preparazione al debug di librerie di classi:  
  
- [Building a Debug Version](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
- [Mixed-Mode Debugging](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
- [Changing Default Configurations](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
- [Modalità di Debug della DLL](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
- [The Calling Application](#vxtskdebuggingdllprojectsthecallingapplication)  
  
- [Controls on a Web Page](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
- [The Immediate Window](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a Debug Version  
 Indipendentemente dalla modalità di avvio del debug, accertarsi di compilare innanzitutto la versione di debug della DLL e che tale versione si trovi nella posizione prevista dall'applicazione. Anche se ciò potrebbe sembrare ovvio, è importante non omettere questo passaggio in quanto l'applicazione potrebbe rilevare una versione differente della DLL e caricarla. A questo punto, il programma continuerebbe l'esecuzione e non si riuscirebbe a comprendere il motivo per il quale il punto di interruzione non è stato raggiunto. Durante il debug, è possibile controllare le DLL caricate dal programma visualizzando la finestra **Moduli** del debugger. In **questa** finestra sono elencate le DLL o gli EXE caricati nel processo sottoposto a debug. Per altre informazioni, vedere [Procedura: Use the Modules Window](../debugger/how-to-use-the-modules-window.md).  
  
 Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) .  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode Debugging  
 L'applicazione che chiama la DLL può essere scritta in codice gestito o nativo. Se la DLL gestita viene chiamata da codice nativo e si desidera eseguire il debug di entrambi, attivare sia il debugger del codice gestito sia quello del codice nativo. È possibile effettuare questa selezione nella  **\<progetto > pagine delle proprietà** finestra o nella finestra di dialogo. L'esecuzione di questa operazione varia a seconda che il debug venga avviato dal progetto della DLL o da quello dell'applicazione chiamante. Per altre informazioni, vedere [Procedura: Eseguire il debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing Default Configurations  
 Quando si crea un progetto di applicazione console mediante il modello di progetto, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio. Se necessario, è possibile modificare tali impostazioni. Per altre informazioni, vedere [impostazioni di progetto per una configurazione di Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [impostazioni di progetto per C# Debug Configurations](../debugger/project-settings-for-csharp-debug-configurations.md), [le impostazioni di progetto per un Debug di Visual Basic Configuration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), e [come: Impostare configurazioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Modalità di Debug della DLL  
 In ciascun progetto descritto in questa sezione viene creata una DLL. Le DLL non possono essere eseguite direttamente, ma devono essere chiamate da un'applicazione, in genere un file EXE. Per altre informazioni, vedere [Creating and Managing Visual C++ Projects](http://msdn.microsoft.com/library/11003cd8-9046-4630-a189-a32bf3b88047). L'applicazione chiamante può soddisfare uno dei criteri seguenti:  
  
-   Essere un'applicazione incorporata in un altro progetto della stessa soluzione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] contenente la libreria di classi.  
  
-   Essere un'applicazione esistente già distribuita in un computer di test o di produzione.  
  
-   Trovarsi sul Web ed essere accessibile tramite un URL.  
  
-   Essere un'applicazione Web contenente una pagina Web che incorpora la DLL.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debug dell'applicazione chiamante  
 Per eseguire il debug di una DLL, iniziare con il debug dell'applicazione chiamante, che in genere è un file EXE o un'applicazione Web. Questo debug può essere eseguito in vari modi.  
  
- Se è disponibile un progetto per l'applicazione chiamante, è possibile aprirlo e avviare l'esecuzione dal menu **Debug** . Per altre informazioni, vedere [Procedura: Avviare l'esecuzione](http://msdn.microsoft.com/b0fe0ce5-900e-421f-a4c6-aa44ddae453c).  
  
- Se l'applicazione chiamante è un programma già distribuito in un computer di test o di produzione ed è già in esecuzione, è possibile stabilire una connessione. Utilizzare questa modalità se la DLL è un controllo ospitato in Internet Explorer oppure un controllo in una pagina Web. Per altre informazioni, vedere [Procedura: Connettersi a un processo in esecuzione](http://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).  
  
- È possibile eseguire il debug dal progetto di DLL. Per altre informazioni, vedere [Procedura: Eseguire il debug da un progetto di DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
- È possibile eseguire il debug dalla finestra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Immediate** window. In tal caso, la finestra **Controllo immediato** svolgerà il ruolo dell'applicazione.  
  
  Prima di iniziare il debug dell'applicazione chiamante, è possibile impostare un punto di interruzione nella libreria di classi. Per altre informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Una volta raggiunto il punto di interruzione, è possibile eseguire il codice un'istruzione alla volta, osservandone l'esecuzione in ciascuna riga fino a isolare il problema. Per altre informazioni, vedere [Code Stepping Overview](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  
  
###  <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Controlli in una pagina Web  
 Per eseguire il debug di un controllo in una pagina Web, creare una pagina di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] contenente tale controllo, se non esiste ancora. È quindi possibile impostare punti di interruzione sia nel codice della pagina Web che in quello del controllo e richiamare la pagina Web da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Prima di iniziare il debug dell'applicazione chiamante, è possibile impostare un punto di interruzione nella DLL. Una volta raggiunto il punto di interruzione, è possibile eseguire il codice un'istruzione alla volta, osservandone l'esecuzione in ciascuna riga fino a isolare il problema. Per altre informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> The Immediate Window  
 È possibile valutare le funzioni o i metodi nella DLL senza disporre di un'applicazione chiamante, ma eseguendo il debug in fase di progettazione e utilizzando la finestra **Controllo immediato** . Per eseguire questo tipo di debug, effettuare le seguenti operazioni dopo avere aperto il progetto di DLL:  
  
1.  Visualizzare la finestra di controllo **immediato** del debugger.  
  
2.  Per testare un metodo denominato `Test` nella classe `Class1`, creare un'istanza di un oggetto di tipo `Class1` digitando il codice C# seguente nella finestra Controllo immediato. Questo codice gestito funziona per Visual Basic e C++ con opportune modifiche alla sintassi:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     In C# tutti i nomi devono essere completi. Inoltre, i metodi o le variabili devono trovarsi nell'ambito e nel contesto correnti della sessione di debug.  
  
3.  Se `Test` accetta un parametro `int` , valutare `Test` usando la finestra **Controllo immediato** :  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Il risultato verrà indicato nella finestra di controllo **immediato**.  
  
4.  Se si desidera continuare a eseguire il debug di `Test` , inserire un punto di interruzione nel metodo e valutare di nuovo la funzione:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Quando verrà raggiunto il punto di interruzione, sarà possibile eseguire `Test`un'istruzione alla volta. Al termine dell'esecuzione di `Test`, nel debugger verrà ripristinata la modalità di progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)
