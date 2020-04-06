---
title: Aggiunta di elementi alle finestre di dialogo Aggiungi nuovo elemento Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710222"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento
Il processo per l'aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento** inizia con le chiavi del Registro di sistema. Come illustrato nelle seguenti voci del Registro di sistema, la sezione **AddItemTemplates** contiene il percorso e il nome della directory in cui vengono inseriti gli elementi resi disponibili nella finestra di dialogo **Aggiungi nuovo elemento.**

> [!NOTE]
> La tabella immediatamente successiva al segmento di codice contiene informazioni aggiuntive sulla voce del Registro di sistema.

 Questa sezione si trova in **HKEY_LOCAL_MACHINE SOFTWARE**.

 Il primo GUID è il CLSID per i progetti di questo tipo. il secondo GUID indica il tipo di progetto registrato per i modelli Aggiungi elementi:

 **\\C061DB26-5833-11D2-96F5-000000000000000 \\Modelli AddItemTemplatesDir\\\\- ACEF4EB2-57CF-11D2-96F4-00000000000001\\**

 **@**- #6

 **TemplatesDir** = \\&lt;Percorso di&gt;\\installazione\\&lt;di&gt;\\&lt;Visual&gt;\\&lt;Studio&gt;\\&lt;SDK VSIntegration SomePackage SomeProject SomeProjectItems&gt;

 **SortPriority** - dword:00000064

| Nome | Type | Dati (dal file *.rgs)* | Descrizione |
|------------------|-----------| - | - |
| (Predefinito) | REG_SZ | %IDS_ADDITEM_TEMPLATES_ENTRY% | ID risorsa per i modelli **Aggiungi elemento.** |
| Modelli ValDir | REG_SZ | %TEMPLATE_PATH%\\&lt;Elementi di progetto SomeProject&gt; | Percorso degli elementi di progetto visualizzati nella finestra di dialogo per la procedura guidata **Aggiungi nuovo elemento.** |
| Val SortPriority | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | Determina l'ordinamento nel nodo della struttura ad albero dei file visualizzati nella finestra di dialogo **Aggiungi nuovo elemento.** |

> [!NOTE]
> I GUID per i tipi di progetto di Visual C e Visual Basic sono i seguenti:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: "FAE04EC0-301F-11D3-BF4B-00C04F79EFBC"
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: F184B08F-C81C-45F6-A57F-5ABD9991F28F

 La directory elencata per **TemplatesDir**, ovvero *\\&lt;%TEMPLATE_PATH% SomeProjectItems&gt;*, è il nodo sul lato sinistro della struttura della finestra di dialogo **Aggiungi nuovo elemento.** Gli elementi aggiuntivi nell'albero sono basati sulla sottodirectory all'interno di tale directory radice. I file disponibili per essere aggiunti al progetto sono gli elementi nel riquadro destro della finestra di dialogo **Aggiungi nuovo elemento.**

 In genere, questa cartella conterrà i file di modello per il progetto, ad esempio un modello HTML o *cpp* file e tutti i file *vsz* per l'avvio di procedure guidate. Per controllare la modalità di visualizzazione degli elementi, è anche possibile includere file *VSDIR* per la localizzazione di icone e nomi di directory. La stringa localizzata è la didascalia visualizzata nella finestra di dialogo che rappresenta questo nodo nella struttura della finestra di dialogo **Aggiungi nuovo elemento.**

 Tuttavia, non è necessario disporre di tutto in un file *VSDIR.* È possibile avere un file *VSDIR* per ogni elemento nella directory. Per ulteriori informazioni, vedere [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) e File di descrizione della directory dei modelli (con estensione [vsdir).](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

> [!NOTE]
> I file *VSDIR* nelle directory dei modelli sono facoltativi. Se si desidera solo inserire un elemento di progetto nella directory e visualizzarlo nella finestra di dialogo **Aggiungi nuovo elemento,** è possibile inserire tale file nella directory dei modelli specificata nell'istruzione **TemplatesDir.** Il file verrà quindi visualizzato nel riquadro destro della finestra di dialogo **Aggiungi nuovo elemento** per il progetto. Tuttavia, se si desidera visualizzare una didascalia localizzata per il file o un'icona, è necessario includere almeno un file *VSDIR* nella directory dei modelli.

## <a name="group-project-items"></a>Raggruppare gli elementi del progetto
 Se si desidera contenere gruppi di modelli nelle cartelle nella struttura della finestra di dialogo **Aggiungi nuovo elemento,** è necessario disporre di sottodirectory nella directory dei modelli radice con gli elementi in esse contenuti. Quando la finestra di dialogo **Aggiungi nuovo elemento** viene visualizzata agli utenti, verranno visualizzate anche le sottocartelle e potranno selezionare gli elementi del progetto da essi.

 La priorità di ordinamento nel segmento di codice determina la posizione in cui verrà creata questa directory del modello nella struttura ad albero rispetto ad altri elementi del nodo della struttura ad albero. Per la finestra di dialogo **Aggiungi nuovo elemento,** la priorità di ordinamento è tutto ciò che è necessario includere in modo che gli elementi verranno visualizzati nella posizione corretta nella finestra di dialogo.

 È inoltre possibile <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> implementare l'interfaccia per filtrare gli elementi visualizzati nella finestra di dialogo **Aggiungi nuovo elemento.** Implementando questa interfaccia, è possibile impostare una directory di modelli su disco che contiene, ad esempio, 50 file di modello e procedura guidata. In questo modo, è possibile avere diversi tipi di progetto con 20 file che appartengono a un tipo di progetto, gli altri 30 file che appartengono a un altro tipo di progetto e tutti i file disponibili in un tipo generale di progetto. In questo modo, a seconda del modello di progetto creato, è possibile visualizzare un set diverso di file di modello.

 Ad esempio, in un progetto Visual Basic, è possibile disporre di progetti Web e progetti client. I Web Form non sono elementi utili da aggiungere a un progetto client e Windows Form non sono elementi utili da aggiungere a un progetto server Web. Pertanto, è possibile creare una directory di modello che contiene tutti i file per entrambi i tipi di progetto. Quindi, implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, è possibile nascondere gli elementi che non devono essere visualizzati in base al tipo di progetto o alle impostazioni del progetto nel progetto.

## <a name="filter-project-items"></a>Filtrare gli elementi del progetto
 `IVsFilterAddProjectItemDlg2`fornisce il filtraggio degli elementi nell'albero (riquadro sinistro) e nei file di progetto (riquadro destro) nei modi seguenti:

- In base ai nomi localizzati (didascalie visualizzate nella finestra di dialogo `IVsFilterAddProjectItemDlg`contenuta nel file *VSDIR)* fornita da .

- Con i nomi effettivi dei file e delle cartelle su disco (non `IVsFilterAddProjectItemDlg`localizzato, nessun file *VSDIR)* fornito da .

- Per categoria, `IVsFilterAddProjectItemDlg2`fornito da .

  Per filtrare in base alla categoria, fornire una stringa di categoria a un elemento nel file *VSDIR,* ad esempio *Web Form* o *elemento Client* in Visual Basic. Il codice della finestra di dialogo recupera quindi la classificazione di categoria dal file *VSDIR* e la passa all'utente. È quindi possibile passare tali `IVsFilterAddProjectItemDlg2` informazioni all'implementazione di per filtrare la finestra di dialogo **Aggiungi nuovo elemento** per categorie. È inoltre possibile filtrare gli elementi per le pagine Web o come casi di applicazione Win32 client. Inoltre, è possibile [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] identificare gli elementi con tag come elementi Microsoft Foundation Classes (MFC) o libreria di modelli attivi (ATL). Quando si identificano questi elementi, il sistema del progetto può definire le proprie classificazioni in modo che il sistema possa essere filtrato in base a categorie e classificazioni.

  Se si implementa questa funzionalità di filtro, non è necessario eseguire il mapping di una tabella di ogni elemento che deve essere nascosto. È possibile classificare semplicemente gli elementi in tipi e inserire le classificazioni nel file *vsdir* o nei file. È quindi possibile nascondere qualsiasi elemento con una classificazione specifica implementando l'interfaccia. In questo modo, è possibile rendere dinamici gli elementi nella finestra di dialogo **Aggiungi nuovo elemento** in base allo stato all'interno del progetto.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Aggiungere modelli di progetto e di elemento di progettoAdd project and project item templates](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [File di descrizione della directory dei modelli (con estensione vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [File della procedura guidata (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
