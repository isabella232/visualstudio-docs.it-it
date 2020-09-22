---
title: Aggiunta di elementi alle finestre di dialogo Aggiungi nuovo elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdacfc4ac65e0dc18512bfb56eb870545c66a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839452"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Aggiunta di elementi nelle finestre di dialogo Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il processo per l'aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento** inizia con le chiavi del registro di sistema. Come illustrato nelle voci del registro di sistema seguenti, la sezione AddItemTemplates contiene il percorso e il nome della directory in cui vengono inseriti gli elementi resi disponibili nella finestra di dialogo **Aggiungi nuovo elemento** .  
  
> [!NOTE]
> La tabella che segue immediatamente il segmento di codice contiene informazioni aggiuntive sulla voce del registro di sistema.  
  
 Questa sezione si trova in [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Il primo GUID è il CLSID per i progetti di questo tipo. il secondo GUID indica il tipo di progetto registrato per i modelli di aggiunta di elementi.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \ 1  
  
 @ = "#6"  
  
 "TemplatesDir" = " \< percorso di installazione di Visual Studio SDK \\ \VSIntegration \\ \SomeFolder \\ \SomePackage \\ \SomeProject \\ \SomeProjectItems"  
  
 "SortPriority" = DWORD: 00000064  
  
|Nome|Type|Dati (dal file RGS)|Descrizione|  
|----------|----------|-----------------------------|-----------------|  
|@ (Impostazione predefinita)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY%|ID risorsa per i modelli **Aggiungi elemento** .|  
|Val TemplatesDir|REG_SZ|% TEMPLATE_PATH% \ SomeProjectItems|Percorso degli elementi del progetto visualizzati nella finestra di dialogo per la procedura guidata **Aggiungi nuovo elemento** .|  
|Val SortPriority|REG_DWORD|100 ( [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)] )|Determina il tipo di ordinamento nel nodo della struttura ad albero dei file visualizzati nella finestra di dialogo **Aggiungi nuovo elemento** .|  
  
> [!NOTE]
> I GUID per i tipi di progetto Visual C# e Visual Basic sono i seguenti: [!INCLUDE[csprcs](../../includes/csprcs-md.md)] : {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] : {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 La directory elencata per TemplateDirs, che è% TEMPLATE_PATH% \ SomeProjectItems, è il nodo sul lato sinistro dell'albero della finestra di dialogo **Aggiungi nuovo elemento** . Gli elementi aggiuntivi nell'albero sono basati sulla sottodirectory all'interno della directory radice. I file disponibili per l'aggiunta al progetto sono gli elementi nel riquadro destro della finestra di dialogo **Aggiungi nuovo elemento** .  
  
 In genere, questa cartella conterrà i file modello per il progetto, ad esempio un file HTML o cpp del modello e qualsiasi file con estensione vsz per l'avvio delle procedure guidate. Per controllare la modalità di visualizzazione degli elementi, è anche possibile includere file con estensione VSDIR per la localizzazione di nomi di directory e icone. La stringa localizzata è la didascalia che viene visualizzata nella finestra di dialogo che rappresenta questo nodo nella struttura ad albero della finestra di dialogo Aggiungi nuovo elemento.  
  
 Tuttavia, non è necessario disporre di tutti gli elementi in un file con estensione VSDIR. È possibile disporre di un file con estensione VSDIR per ogni elemento nella directory. Per ulteriori informazioni, vedere [procedura guidata (. VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md) Descrizione della directory di file e [modelli (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
> I file con estensione VSDIR nelle directory dei modelli sono facoltativi. Se si vuole semplicemente inserire un elemento di progetto nella directory e visualizzarlo nella finestra di dialogo **Aggiungi nuovo elemento** , è possibile inserire il file nella directory dei modelli specificata nell'istruzione TemplatesDir. Il file verrà quindi visualizzato nel riquadro destro della finestra di dialogo **Aggiungi nuovo elemento** per il progetto. Tuttavia, se si desidera visualizzare una didascalia localizzata per il file o un'icona, è necessario includere almeno un file con estensione VSDIR nella directory Templates.  
  
## <a name="grouping-project-items"></a>Raggruppamento di elementi di progetto  
 Se si desidera contenere gruppi di modelli in cartelle nell'albero della finestra di dialogo **Aggiungi nuovo elemento** , è necessario disporre di sottodirectory nella directory del modello radice con gli elementi in essi contenuti. Quando viene visualizzata la finestra di dialogo **Aggiungi nuovo elemento** , gli utenti visualizzeranno anche le sottocartelle e potranno selezionare gli elementi del progetto.  
  
 La priorità di ordinamento nel segmento di codice determina la posizione in cui verrà creata la directory del modello nell'albero rispetto ad altri elementi del nodo della struttura ad albero. Per la finestra di dialogo **Aggiungi nuovo elemento** , è necessario includere la priorità di ordinamento in modo che gli elementi vengano visualizzati nella posizione corretta nella finestra di dialogo.  
  
 È anche possibile implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaccia per filtrare gli elementi visualizzati nella finestra di dialogo **Aggiungi nuovo elemento** . Implementando questa interfaccia, è possibile configurare una directory dei modelli su disco contenente, ad esempio, i file di modello e di procedura guidata 50. In questo modo, è possibile disporre di tipi di progetto diversi con 20 file che appartengono a un tipo di progetto, gli altri 30 file che appartengono a un altro tipo di progetto e tutti i file disponibili in un tipo generale di progetto. In questo modo, a seconda del modello di progetto creato, è possibile visualizzare un set di file modello diverso.  
  
 Ad esempio, in un progetto di Visual Basic, è possibile che siano presenti progetti Web e progetti client. I Web Form non sono elementi utili da aggiungere a un progetto client e Windows Form non sono elementi utili da aggiungere a un progetto server Web. Pertanto, è possibile creare una directory del modello che contiene tutti i file per entrambi i tipi di progetto. Implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> , è quindi possibile nascondere elementi che non devono essere visualizzati in base al tipo di progetto o alle impostazioni del progetto nel progetto.  
  
## <a name="filtering-project-items"></a>Filtraggio di elementi di progetto  
 `IVsFilterAddProjectItemDlg2` consente di filtrare gli elementi nel riquadro sinistro e i file di progetto (riquadro a destra) nei modi seguenti:  
  
- In base ai nomi localizzati, ovvero le didascalie visualizzate nella finestra di dialogo contenuta nel file VSDIR, fornite da `IVsFilterAddProjectItemDlg` .  
  
- In base ai nomi effettivi dei file e delle cartelle su disco (non localizzato-nessun file VSDIR) fornito da `IVsFilterAddProjectItemDlg` .  
  
- Per categoria, fornito da `IVsFilterAddProjectItemDlg2` .  
  
  Per filtrare in base alla categoria, fornire una stringa di categoria a un elemento nel file con estensione VSDIR, ad esempio "Web Form" o "elemento client" in Visual Basic. Il codice della finestra di dialogo Recupera quindi la classificazione Category dal file VSDIR e la passa all'utente. È quindi possibile passare le informazioni all'implementazione di `IVsFilterAddProjectItemDlg2` per filtrare la finestra di dialogo **Aggiungi nuovo elemento** in base alle categorie. È anche possibile filtrare gli elementi per le pagine Web o come casi di applicazioni Win32 client. Inoltre, è possibile identificare [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] gli elementi contrassegnati come Microsoft Foundation Classes (MFC) o gli elementi ATL (Active Template Library). Quando si identificano questi elementi, il sistema del progetto può definire le proprie classificazioni in modo che il sistema possa essere filtrato in base alle categorie e alle classificazioni.  
  
  Se si implementa questa funzionalità di filtro, non è necessario eseguire il mapping di una tabella di ogni elemento che deve essere nascosto. È possibile classificare semplicemente gli elementi in tipi e inserire le classificazioni nel file o nei file VSDIR. È quindi possibile nascondere gli elementi che hanno una classificazione specifica implementando l'interfaccia. In questo modo, è possibile rendere dinamici gli elementi nella finestra di dialogo **Aggiungi nuovo elemento** in base allo stato all'interno del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrazione di modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID per gli oggetti che in genere vengono usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Descrizione Directory modello (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
