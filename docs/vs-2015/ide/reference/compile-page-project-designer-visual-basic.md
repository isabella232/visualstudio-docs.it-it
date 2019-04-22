---
title: Pagina Compilazione, Creazione progetti (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 65
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3dd58013cb26e8533a5b898a0e5cd1df3be1b262
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649056"
---
# <a name="compile-page-project-designer-visual-basic"></a>Compilazione (pagina), Creazione progetti (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare la pagina **Compilazione** in Creazione progetti per specificare le istruzioni di compilazione. In questa pagina è anche possibile specificare opzioni del compilatore avanzate ed eventi di pre-compilazione o post-compilazione.  
  
 Per accedere alla pagina **Compilazione**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Quindi scegliere **Progetto**, **Proprietà** sulla barra dei menu. Quando viene visualizzata la finestra Creazione progetti, fare clic sulla scheda **Compilazione**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Configurazione e Piattaforma  
 Le impostazioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
> [!NOTE]
>  Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Gli elenchi **Configurazione** e **Piattaforma** non vengono pertanto visualizzati. Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni sono **Debug** (impostazione predefinita), **Rilascio** o **Tutte le configurazioni**. Per altre informazioni, vedere [Debug e Release Project Configurations](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) e [come: Creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare. È possibile specificare **Qualsiasi CPU** (impostazione predefinita), **x64** o **x86**. Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
## <a name="compiler-configuration-options"></a>Opzioni di configurazione del compilatore  
 Le impostazioni seguenti consentono di impostare le opzioni di configurazione del compilatore.  
  
 **Percorso dell'output di compilazione**  
 Specifica il percorso dei file di output per la configurazione del progetto. Digitare il percorso dell'output di compilazione in questa casella oppure fare clic sul pulsante **Sfoglia** per selezionare un percorso. Si noti che il percorso è relativo. Se si immette un percorso assoluto, sarà salvato come relativo. Il percorso predefinito è bin\Debug\ o bin\Release\\. Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Scegliendo il comando **Compila** dal menu **Debug** (F5) la compilazione verrà inserita nel percorso di debug indipendentemente dal **Percorso output** specificato. Il comando **Compila** del menu **Compila** la inserisce invece nel percorso specificato. Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 **Option Explicit**  
 Specifica se consentire la dichiarazione implicita delle variabili. Selezionare **On** per richiedere la dichiarazione esplicita delle variabili. In questo modo il compilatore segnala errori se le variabili non vengono dichiarate prima dell'uso. Selezionare **Off** per consentire la dichiarazione implicita delle variabili.  
  
 Questa impostazione corrisponde all'opzione del compilatore [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7).  
  
 Se un file di codice sorgente contiene un'[istruzione Option Explicit](http://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc), il valore `On` o `Off` nell'istruzione sostituisce l'impostazione di **Option Explicit** nella **pagina Compilazione**.  
  
 Quando si crea un progetto, l'impostazione **Option Explicit** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Explicit** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Explicit** in **Impostazioni predefinite di Visual Basic** è **On**.  
  
 L'impostazione di **Option Explicit** su `Off` non è in genere consigliabile. È possibile digitare un nome di variabile in modo errato in una o più posizioni e ciò può causare risultati imprevisti quando viene eseguito il programma.  
  
 **Option Strict**  
 Specifica se applicare la semantica rigorosa per i tipi. Quando **Option Strict** è **On**, le condizioni seguenti causano un errore in fase di compilazione:  
  
- Conversioni implicite verso un tipo di dati più piccolo  
  
- Associazione tardiva  
  
- Tipizzazione implicita che comporta un tipo `Object`  
  
  Questi errori si verificano in presenza di una conversione implicita verso un tipo di dati più piccolo. Per altre informazioni, vedere [Option Strict Statement](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) (Istruzione Open Strict), [Conversioni implicite ed esplicite](http://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66) e [Widening and Narrowing Conversions](http://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd) (Conversioni verso un tipo di dati più grande e più piccolo).  
  
  Un oggetto è ad associazione tardiva quando viene assegnato a una proprietà o a un metodo di una variabile dichiarata di tipo `Object`. Per altre informazioni, vedere [Option Strict Statement](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) (Istruzione Option Strict) e [Associazione anticipata e tardiva](http://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).  
  
  Si verificano errori di tipo di oggetto implicito quando non è possibile dedurre un tipo appropriato per una variabile dichiarata, pertanto viene dedotto il tipo `Object`. Questo errore si verifica principalmente quando si usa un'istruzione `Dim` per dichiarare una variabile senza usare una clausola `As` e `Option Infer` è Off. Per altre informazioni, vedere [Option Strict Statement](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) (Istruzione Option Strict), [Option Infer Statement](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652) (Istruzione Open Infer) e [Visual Basic Language Specification](http://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df) (Specifica del linguaggio Visual Basic).  
  
  L'impostazione **Option Strict** corrisponde all'opzione del compilatore [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da).  
  
  Se un file di codice sorgente contiene un'[istruzione Option Strict](http://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), il valore `On` o `Off` nell'istruzione sostituisce l'impostazione di **Option Strict** nella **pagina Compilazione**.  
  
  Quando si crea un progetto, l'impostazione **Option Strict** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Strict** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Strict** in **Impostazioni predefinite di Visual Basic** è **Off**.  
  
  **Singoli avvisi di Option Strict.** La sezione **Configurazioni avvisi** della **pagina Compilazione** include impostazioni corrispondenti alle tre condizioni che causano un errore in fase di compilazione quando `Option Strict` è On. Queste impostazioni sono le seguenti:  
  
- **Conversione implicita**  
  
- **Binding tardivo. La chiamata potrebbe non riuscire in fase di esecuzione.**  
  
- **Tipo implicito. Verrà utilizzato oggetto.**  
  
  Quando si imposta **Option Strict** su **On**, tutte e tre queste impostazioni di configurazione degli avvisi vengono impostate su **Errore**. Quando si imposta **Option Strict** su **Off**, tutte e tre le impostazioni vengono impostate su **Nessuno**.  
  
  È possibile modificare singolarmente ogni impostazione di configurazione degli avvisi su **Nessuno**, **Avviso** o **Errore**. Se tutte e tre le impostazioni di configurazione degli avvisi vengono impostate su **Errore**, nella casella `Option strict` viene visualizzato `On`. Se tutte e tre sono impostate su **Nessuno**, nella casella viene visualizzato `Off`. Per qualsiasi altra combinazione di queste impostazioni, viene visualizzato **(personalizzato)**.  
  
  **Option Compare**  
  Specifica il tipo di confronto di stringhe da usare. Selezionare **Binario** per indicare al compilatore di usare confronti di stringhe binari con distinzione tra maiuscole e minuscole. Selezionare **Testo** per usare confronti di stringhe di testo specifici delle impostazioni locali senza distinzione tra maiuscole e minuscole.  
  
  Questa impostazione corrisponde all'opzione del compilatore [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4).  
  
  Se un file di codice sorgente contiene un'[istruzione Option Compare](http://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e), il valore `Binary` o `Text` nell'istruzione sostituisce l'impostazione di **Option Compare** nella **pagina Compilazione**.  
  
  Quando si crea un progetto, l'impostazione **Option Compare** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Compare** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Compare** in **Impostazioni predefinite di Visual Basic** è **Binario**.  
  
  **Option Infer**  
  Specifica se consentire l'inferenza del tipo di variabile locale nelle dichiarazioni di variabile. Selezionare **On** per consentire l'uso dell'inferenza del tipo di variabile locale. Selezionare **Off** per impedire l'inferenza del tipo di variabile locale.  
  
  Questa impostazione corrisponde all'opzione del compilatore [/optioninfer](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed).  
  
  Se un file di codice sorgente contiene un'[istruzione Option Infer](http://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652), il valore `On` o `Off` nell'istruzione sostituisce l'impostazione di **Option Infer** nella **pagina Compilazione**.  
  
  Quando si crea un progetto, l'impostazione **Option Infer** nella **pagina Compilazione** viene impostata sul valore dell'impostazione **Option Infer** nella finestra di dialogo **Opzioni**. Per visualizzare o modificare l'impostazione in questa finestra di dialogo scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, quindi fare clic su **Impostazioni predefinite di Visual Basic**. L'impostazione predefinita iniziale di **Option Infer** in **Impostazioni predefinite di Visual Basic** è **On**.  
  
  **CPU di destinazione**  
  Specifica il processore da impostare come destinazione del file di output. Specificare **x86** per qualsiasi processore compatibile con Intel a 32 bit, **x64** per qualsiasi processore compatibile con Intel a 64 bit, **ARM** per processori ARM oppure **Qualsiasi CPU** per specificare che qualsiasi processore è accettabile. **Qualsiasi CPU** è il valore predefinito per i nuovi progetti, in quanto consente all'applicazione di essere eseguita sul maggior numero di tipi di hardware.  
  
  Per altre informazioni, vedere [/platform (Visual Basic)](http://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).  
  
  **Preferisci 32 bit**  
  Se la casella di controllo **Preferisci 32 bit** è selezionata, l'applicazione viene eseguita come applicazione a 32 bit sia nelle versioni di Windows a 32 bit sia in quelle a 64 bit. In caso contrario, l'applicazione viene eseguita come applicazione a 32 bit su versioni di Windows a 32 bit e come applicazione a 64 bit su versioni di Windows a 64 bit.  
  
  L'esecuzione come applicazione a 64 bit raddoppia le dimensioni del puntatore e può causare problemi di compatibilità con le librerie che sono esclusivamente a 32 bit. È opportuno eseguire un'applicazione a 64 bit solo se viene eseguita con una velocità significativamente maggiore oppure se richiede più di 4 GB di memoria.  
  
  Questa casella di controllo è disponibile solo se tutte le condizioni seguenti sono true:  
  
- Nella **pagina Compilazione** l'elenco **CPU destinazione** è impostato su **Qualsiasi CPU**.  
  
- Nella **pagina Applicazione** l'elenco **Tipo di applicazione** specifica che il progetto è un'applicazione.  
  
- Nella **pagina Applicazione** l'elenco **Framework di destinazione** specifica .NET Framework 4.5.  
  
  **Configurazioni avvisi**  
  La tabella seguente elenca le condizioni di compilazione e il livello di notifica corrispondente **Nessuno**, **Avviso** o **Errore** per ognuna.  
  
  Per impostazione predefinita, tutti gli avvisi del compilatore vengono aggiunti all'Elenco attività durante la compilazione. Selezionare **Disabilita tutti gli avvisi** per indicare al compilatore di non generare avvisi o errori. Selezionare **Considera tutti gli avvisi come errori** se si vuole che il compilatore consideri gli avvisi come errori che devono essere corretti.  
  
  **Disabilita tutti gli avvisi**  
  Specifica se consentire al compilatore di generare notifiche come specificato nella tabella **Condizione e notifica** descritta in precedenza in questo documento. Per impostazione predefinita, questa casella di controllo è deselezionata. Selezionare questa casella di controllo per indicare al compilatore di non generare avvisi o errori.  
  
  Questa impostazione corrisponde all'opzione del compilatore [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).  
  
  **Considera tutti gli avvisi come errori**  
  Specifica come considerare gli avvisi. Per impostazione predefinita, questa casella di controllo è deselezionata, in modo che tutte le notifiche di avviso rimangano impostate su **Avviso**. Selezionare questa casella di controllo per impostare tutte le notifiche di avviso su **Errore**.  
  
  Questa opzione è disponibile solo se **Disabilita tutti gli avvisi** è deselezionata.  
  
  **Genera il file di documentazione XML**  
  Specifica se generare le informazioni di documentazione. Per impostazione predefinita, questa casella di controllo è selezionata, per indicare al compilatore di generare informazioni di documentazione e includerle in un file XML. Deselezionare questa casella di controllo per indicare al compilatore di non creare la documentazione.  
  
  Questa impostazione corrisponde all'opzione del compilatore [/doc](http://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).  
  
  **Registra per interoperabilità COM**  
  Specifica se l'applicazione gestita esporrà un oggetto COM (COM Callable Wrapper) che consente a un oggetto COM di interagire con l'applicazione.  
  
  Per impostazione predefinita, questa casella di controllo è deselezionata, a indicare che l'applicazione non consentirà l'interoperabilità COM. Selezionare questa casella di controllo per consentire l'interoperabilità COM.  
  
  Questa opzione non è disponibile per i progetti Applicazione Windows o Applicazione console.  
  
  **Eventi di compilazione**  
  Fare clic su questo pulsante per accedere alla finestra di dialogo **Eventi di compilazione**. Usare questa finestra di dialogo per specificare le istruzioni di configurazione pre-compilazione e post-compilazione per il progetto. Questa finestra di dialogo si applica esclusivamente ai progetti Visual Basic. Per altre informazioni, vedere [Finestra di dialogo Eventi di compilazione (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
  **Opzioni di compilazione avanzate**  
  Fare clic su questo pulsante per accedere alla finestra di dialogo **Impostazioni del compilatore avanzate**. Usare la finestra di dialogo **Impostazioni del compilatore avanzate** per specificare le proprietà avanzate di configurazione della compilazione per un progetto. Questa finestra di dialogo si applica esclusivamente ai progetti Visual Basic. Per altre informazioni, vedere [Finestra di dialogo Impostazioni del compilatore avanzate (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il debug e il rilascio delle configurazione del progetto](http://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)   
 [Gestione delle proprietà di compilazione](http://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Procedura: Specificare eventi di compilazione (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Visual Basic Command-Line Compiler](http://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)  (Compilatore da riga di comando di Visual Basic)  
 [Procedura: Creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)
