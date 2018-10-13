---
title: Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d45431d2d6757169c225136620124d94a6e75dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223106"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Aggiunta di elementi nelle finestre di dialogo Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il processo per l'aggiunta di elementi per il **Aggiungi nuovo elemento** viene avviata la finestra di dialogo con le chiavi del Registro di sistema. Come illustrato nelle voci del Registro di sistema seguenti, la sezione AddItemTemplates contiene il percorso e nome della directory degli elementi reso disponibile nel **Aggiungi nuovo elemento** vengono inseriti nella finestra di dialogo.  
  
> [!NOTE]
>  La tabella che segue immediatamente il segmento di codice contiene informazioni aggiuntive relative alla voce del Registro di sistema.  
  
 In questa sezione è disponibile in [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 Il primo GUID è il CLSID per i progetti di questo tipo. il GUID secondo indica il tipo di progetto registrati per i modelli di aggiungere elementi.  
  
 \\\1 \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} {C061DB26-5833-11D2-96F5-000000000000}  
  
 @="#6"  
  
 "TemplatesDir"="\<percorso di installazione di Visual Studio SDK\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" = dword:00000064  
  
|nome|Tipo|Dati (dal file con estensione RGS)|Descrizione|  
|----------|----------|-----------------------------|-----------------|  
|@ (Impostazione predefinita)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|ID risorsa per **Aggiungi elemento** modelli.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Percorso degli elementi di progetto visualizzato nella finestra di dialogo per la **Aggiungi nuovo elemento** procedura guidata.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../includes/vcprx64-md.md)])|Determina l'ordine di ordinamento nel nodo della struttura dei file visualizzati nei **Aggiungi nuovo elemento** nella finestra di dialogo.|  
  
> [!NOTE]
>  I GUID per i tipi di progetto Visual c# e Visual Basic sono i seguenti:[!INCLUDE[csprcs](../../includes/csprcs-md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 La directory elencate per TemplateDirs, ovvero % TEMPLATE_PATH%\SomeProjectItems, è il nodo sul lato sinistro della **Aggiungi nuovo elemento** struttura ad albero casella di dialogo. Elementi aggiuntivi dell'albero si basano sulla sottodirectory della directory radice. I file possono essere aggiunti al progetto sono gli elementi nel riquadro di destra del **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 In genere, questa cartella conterrà i file di modello per il progetto, ad esempio un modello HTML o file con estensione cpp e tutti i file con estensione vsz per l'avvio di procedure guidate. Per controllare come vengono visualizzati gli elementi, è anche possibile includere file VSDIR per la localizzazione di icone e i nomi di directory. La stringa localizzata è la didascalia visualizzata nella finestra di dialogo che rappresenta questo nodo nell'albero della finestra di dialogo Aggiungi nuovo elemento.  
  
 Tuttavia, non è necessario disporre di tutto in un unico file VSDIR. È possibile avere un file VSDIR per ogni elemento nella directory. Per altre informazioni, vedere [Wizard (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) e [Descrizione Directory del modello (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  I file VSDIR nelle directory di modello sono facoltativi. Se si desidera inserire un elemento di progetto nella directory e lo visualizza nel **Aggiungi nuovo elemento** nella finestra di dialogo è possibile inserire file nella directory di modelli specificate nell'istruzione TemplatesDir. Il file verrà quindi visualizzato nel riquadro di destra del **Aggiungi nuovo elemento** finestra di dialogo per il progetto. Tuttavia, se si desidera visualizzare un titolo per il file o un'icona localizzato, è necessario includere almeno un file VSDIR nella directory di modelli.  
  
## <a name="grouping-project-items"></a>Elementi di progetto di raggruppamento  
 Se si desidera contengono gruppi di modelli in cartelle nel **Aggiungi nuovo elemento** struttura ad albero casella di dialogo, è necessario disporre le sottodirectory nella directory radice modello con gli elementi in essi contenuti. Quando la **Aggiungi nuovo elemento** agli utenti verrà visualizzata la finestra di dialogo, verrà inoltre vedere le sottocartelle ed essere in grado di selezionare gli elementi di progetto da esse.  
  
 La priorità di ordinamento nel segmento di codice determina dove verrà creata la directory dei modelli nella struttura della relazione ad altri elementi del nodo dell'albero. Per il **Aggiungi nuovo elemento** finestra di dialogo, la priorità di ordinamento è tutto ciò che è necessario includere in modo che gli elementi verranno visualizzati nella posizione corretta nella finestra di dialogo.  
  
 È anche possibile implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> per filtrare gli elementi visualizzati nell'interfaccia di **Aggiungi nuovo elemento** nella finestra di dialogo. Implementando questa interfaccia, è possibile impostare un modello di directory sul disco che contiene, ad esempio, 50 file di modello e procedura guidata. In tal modo, è possibile avere diversi tipi di progetto con 20 file che appartengono a un tipo di progetto, altri 30 file che appartengono a un altro tipo di progetto e tutti i file disponibili in un tipo generale del progetto. In questo modo, a seconda di quale progetto modello creato, è possibile visualizzare un set diverso di file di modello.  
  
 In un progetto di Visual Basic, ad esempio, si potrebbe essere i progetti Web e client. Web Form non sono elementi utili da aggiungere a un progetto di client e windows form non sono elementi utili da aggiungere a un progetto di server Web. Pertanto, è possibile creare una directory del modello che contiene tutti i file per entrambi i tipi di progetto. Quindi implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, è possibile nascondere gli elementi che non devono essere visualizzati in base al tipo di progetto o le impostazioni di progetto nel progetto.  
  
## <a name="filtering-project-items"></a>Filtraggio degli elementi di progetto  
 `IVsFilterAddProjectItemDlg2` sono disponibili per il filtraggio degli elementi nella struttura ad albero (riquadro a sinistra) e i file di progetto (riquadro a destra) nei modi seguenti:  
  
-   Per i nomi localizzati (didascalie da visualizzare nella finestra di dialogo che è contenuta nel file VSDIR) fornita dal `IVsFilterAddProjectItemDlg`.  
  
-   Per i nomi effettivi dei file e cartelle su disco (non localizzato, ovvero nessun file VSDIR) fornita da `IVsFilterAddProjectItemDlg`.  
  
-   In base alla categoria, fornito da `IVsFilterAddProjectItemDlg2`.  
  
 Per filtrare in base alla categoria, specificare una stringa di categoria per un elemento nel file VSDIR, ad esempio "Web form" o "Elemento Client" in Visual Basic. Il codice della finestra di dialogo, quindi, recupera la classificazione di categoria dal file VSDIR e lo passa all'utente. È quindi possibile passare tali informazioni per l'implementazione di `IVsFilterAddProjectItemDlg2` per filtrare le **Aggiungi nuovo elemento** finestra di dialogo categorie. È anche possibile filtrare gli elementi per le pagine Web o come case di applicazioni client Win32. È anche possibile identificare [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] contrassegnare gli elementi come elementi del modello attivo library (ATL) o Microsoft Foundation Classes (MFC). Quando si rileva questi elementi, il sistema di progetto può definire una proprio le classificazioni in modo che il sistema può essere filtrato in base a categorie e le classificazioni.  
  
 Se si implementa questa funzionalità di filtro, non è necessario eseguire il mapping di una tabella di ogni elemento che deve essere nascosto. È semplicemente possibile classificare gli elementi in tipi e inserire le classificazioni nel file VSDIR o dei file. È quindi possibile nascondere gli elementi che hanno una specifica classificazione implementando l'interfaccia. In questo modo, è possibile rendere gli elementi di **Aggiungi nuovo elemento** dinamico di finestra di dialogo basata sullo stato all'interno del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID per gli oggetti che sono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Descrizione del modello di Directory (. File VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)

