---
title: Pagina Compilazione, Creazione progetti (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aa4eea56321d636efb6458b52b8ad2f271e439ce
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65673841"
---
# <a name="build-page-project-designer-c"></a>Pagina Compilazione, Progettazione progetti (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare la pagina **Compilazione** di **Creazione progetti** per specificare le proprietà di configurazione della compilazione del progetto. Questa pagina è applicabile solo ai progetti [!INCLUDE[csprcs](../../includes/csprcs-md.md)].  
  
 Per accedere alla pagina **Compilazione**, scegliere un nodo del progetto (non il nodo **Soluzione**) in **Esplora soluzioni**. Quindi scegliere **Progetto**, **Proprietà** sulla barra dei menu. Quando si apre Creazione progetti, fare clic sulla scheda **Compilazione**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="configuration-and-platform"></a>Configurazione e Piattaforma  
 Le opzioni seguenti consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
> [!NOTE]
> Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Queste opzioni non sono di conseguenza visualizzate. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare. Le impostazioni possono essere **Attiva (Debug)** (il valore predefinito), **Debug**, **Release** o **Tutte le configurazioni**.  
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare. L'impostazione predefinita è **Active (Any CPU)** (Attiva (qualsiasi CPU)). È possibile modificare la piattaforma attiva tramite **Gestione configurazione**. Per altre informazioni, vedere [How to: Create and Edit Configurations](../../ide/how-to-create-and-edit-configurations.md) (Procedura: Creare e modificare le configurazioni).  
  
## <a name="general"></a>Generale  
 Le opzioni seguenti consentono di configurare diverse impostazioni del compilatore C#.  
  
 **Simboli di compilazione condizionale**  
 Specifica i simboli su cui eseguire la compilazione condizionale. Separare i simboli con un punto e virgola (";"). Per altre informazioni, vedere [/define (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).  
  
 **Definisci costante DEBUG**  
 Definisce DEBUG come simbolo in tutti i file di codice sorgente dell'app. Selezionare questa opzione equivale a usare l'opzione della riga di comando `/define:DEBUG`.  
  
 **Definisci costante TRACE**  
 Definisce TRACE come simbolo in tutti i file di codice sorgente dell'app. Selezionare questa opzione equivale a usare l'opzione della riga di comando `/define:TRACE`.  
  
 **CPU di destinazione**  
 Specifica il processore da impostare come destinazione del file di output. Scegliere **x86** per qualsiasi processore compatibile con Intel a 32 bit, scegliere **x64** per qualsiasi processore compatibile con Intel a 64 bit, scegliere **ARM** per processori ARM oppure scegliere **Any CPU** (Qualsiasi CPU) per specificare che qualsiasi processore è accettabile. **Any CPU** (Qualsiasi CPU) è il valore predefinito per i progetti, in quanto consente all'applicazione di essere eseguita su una vasta gamma di hardware.  
  
 Per altre informazioni, vedere [/platform (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).  
  
 **Preferisci 32 bit**  
 Se la casella di controllo **Preferisci 32 bit** è selezionata, l'applicazione viene eseguita come applicazione a 32 bit sia nelle versioni di Windows a 32 bit sia in quelle a 64 bit. Se la casella di controllo non è selezionata, l'applicazione viene eseguita come applicazione a 32 bit nelle versioni di Windows a 32 bit e come applicazione a 64 bit nelle versioni a 64 bit di Windows.  
  
 Se un'applicazione viene eseguita come applicazione a 64 bit, le dimensioni del puntatore raddoppiano e si possono verificare problemi di compatibilità con altre librerie che sono esclusivamente a 32 bit. È utile eseguire un'applicazione a 64 bit solo se sono necessari più di 4 GB di memoria o se le istruzioni a 64 bit garantiscono un miglioramento significativo delle prestazioni.  
  
 Questa casella di controllo è disponibile solo se tutte le condizioni seguenti sono true:  
  
- Nella **pagina Compilazione** l'elenco **Piattaforma di destinazione** è impostato su **Any CPU** (Qualsiasi CPU).  
  
- Nella **pagina Applicazione** l'elenco **Tipo di Output** specifica che il progetto è un'applicazione.  
  
- Nella **pagina Applicazione** l'elenco **Framework di destinazione** specifica .NET Framework 4.5.  
  
  **Consenti codice unsafe**  
  Consente la compilazione del codice che usa la parola chiave [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0). Per altre informazioni, vedere [/unsafe (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).  
  
  **Ottimizza codice**  
  Abilita o disabilita le ottimizzazioni eseguite dal compilatore per ridurre le dimensioni del file di output e aumentarne la velocità e l'efficienza. Per altre informazioni, vedere [/optimize (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Le impostazioni riportate di seguito sono usate per configurare le opzioni di errori e avvisi del processo di compilazione.  
  
 **Livello avvisi**  
 Specifica il livello da visualizzare per gli avvisi del compilatore. Per altre informazioni, vedere [/warn (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).  
  
 **Non visualizzare avvisi**  
 Blocca la capacità del compilatore di generare uno o più avvisi. Separare più numeri di avvisi tramite virgola o punto e virgola. Per altre informazioni, vedere [/nowarn (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).  
  
## <a name="treat-warnings-as-errors"></a>Considera gli avvisi come errori  
 Le impostazioni riportate di seguito sono usate per specificare quali avvisi considerare come errori. Selezionare una delle opzioni seguenti per indicare in quali condizioni restituire un errore se la compilazione rileva un avviso. Per altre informazioni, vedere [/warnaserror (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).  
  
 **None**  
 Non considera gli avvisi come errori.  
  
 **Avvisi specifici**  
 Considera gli avvisi specificati come errori. Separare più numeri di avvisi tramite virgola o punto e virgola.  
  
 **All**  
 Considera tutti gli avvisi come errori.  
  
## <a name="output"></a>Output  
 Le impostazioni riportate di seguito sono usate per configurare le opzioni di output del processo di compilazione.  
  
 **Percorso output**  
 Specifica il percorso dei file di output per la configurazione del progetto. Immettere il percorso dell'output di compilazione in questa casella, oppure scegliere il pulsante **Sfoglia** per specificare un percorso. Si noti che il percorso è relativo. Se si immette un percorso assoluto, sarà salvato come relativo. Il percorso predefinito è bin\Debug o bin\Release\\. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 Usando configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale. Scegliendo il comando **Compila** dal menu **Debug** (F5) la compilazione verrà inserita nel percorso di debug indipendentemente dal **Percorso output** specificato. Il comando **Compila** del menu **Compila** la inserisce invece nel percorso specificato. Per altre informazioni, vedere [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Eseguire il debug e il rilascio delle configurazione del progetto).  
  
 **File di documentazione XML**  
 Specifica il nome di un file in cui saranno elaborati i commenti relativi alla documentazione. Per altre informazioni, vedere [/doc (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).  
  
 **Registra per interoperabilità COM**  
 Indica che l'applicazione gestita esporrà un oggetto COM (COM Callable Wrapper) che consentirà a un oggetto COM di interagire con l'applicazione gestita. La proprietà **Tipo di output** nella [pagina Applicazione](../../ide/reference/application-page-project-designer-visual-basic.md) di **Creazione progetti** dell'applicazione deve essere impostata su **Libreria di classi** per rendere disponibile la proprietà **Registra per interoperabilità COM**. Per una classe di esempio che è possibile includere nell'applicazione [!INCLUDE[csprcs](../../includes/csprcs-md.md)] ed esporre come oggetto COM, vedere [Example COM Class](https://msdn.microsoft.com/library/6504dea9-ad1c-4993-a794-830fec5270af) (Esempio di classe COM).  
  
 **Genera assembly di serializzazione**  
 Specifica se il compilatore userà lo strumento per la generazione di serializzatori XML (Sgen.exe) per creare assembly di serializzazione XML. Gli assembly di serializzazione possono migliorare le prestazioni di avvio della classe <xref:System.Xml.Serialization.XmlSerializer>, se è stata usata per serializzare i tipi nel codice. Per impostazione predefinita, questa opzione è impostata su **Auto**. Specifica quindi che saranno generati assembly di serializzazione solo se è stata usata la classe <xref:System.Xml.Serialization.XmlSerializer> per codificare i tipi nel codice in XML. **Off** specifica che non saranno mai generati assembly di serializzazione, indipendentemente dal fatto che il codice usi o meno la classe <xref:System.Xml.Serialization.XmlSerializer>. **On** specifica che saranno sempre generati assembly di serializzazione. Gli assembly di serializzazione sono denominati `TypeName`.XmlSerializers.dll. Per altre informazioni, vedere [Strumento per la generazione di serializzatori XML (Sgen.exe)](https://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
 **Avanzate**  
 Selezionare il collegamento per informazioni sulla finestra di dialogo [Impostazioni di compilazione avanzate (C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Project Properties Reference](../../ide/reference/project-properties-reference.md)  (Riferimenti alle proprietà di progetto)  
 [Opzioni del compilatore C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44)
