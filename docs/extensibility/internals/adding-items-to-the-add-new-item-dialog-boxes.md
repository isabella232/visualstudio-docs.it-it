---
title: Aggiunta di elementi alle finestre di dialogo Aggiungi nuovo elemento | Microsoft Docs
description: Informazioni su come aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento in Visual Studio, in modo da poter visualizzare modelli ed elementi di progetto da usare nei progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70bc1a0c4d90d8cab0b2193550773745fc2dd47e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904409"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento
Il processo di aggiunta di elementi alla finestra **di dialogo Aggiungi nuovo elemento** inizia con le chiavi del Registro di sistema. Come illustrato nelle voci del Registro di sistema seguenti, la sezione **AddItemTemplates** contiene  il percorso e il nome della directory in cui vengono inseriti gli elementi resi disponibili nella finestra di dialogo Aggiungi nuovo elemento.

> [!NOTE]
> La tabella immediatamente dopo il segmento di codice contiene informazioni aggiuntive sulla voce del Registro di sistema.

 Questa sezione si trova in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 Il primo GUID è il CLSID per i progetti di questo tipo. Il secondo GUID indica il tipo di progetto registrato per i modelli Aggiungi elementi:

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\ AddItemTemplates \\ TemplatesDir \\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \\ 1**

 **@** = #6

   =  \\ TemplatesDir &lt; Visual Studio percorso di installazione di &gt; \\ VSIntegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; SomeProject &gt; \\ &lt; SomeProjectItems&gt;

 **SortPriority** = dword:00000064

| Nome | Tipo | Dati (dal file *con estensione rgs)* | Descrizione |
|------------------|-----------| - | - |
| @ (impostazione predefinita) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | ID risorsa per i **modelli Aggiungi** elemento. |
| Val TemplatesDir | REG_SZ | %TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | Percorso degli elementi di progetto visualizzati nella finestra di dialogo per la **procedura guidata Aggiungi nuovo** elemento. |
| Val SortPriority | REG_DWORD | 100 ( [!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)] ) | Determina l'ordinamento nel nodo della struttura ad albero dei file visualizzati nella finestra **di dialogo** Aggiungi nuovo elemento . |

> [!NOTE]
> I GUID per i tipi di progetto visual c# e Visual Basic sono i seguenti:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 La directory elencata per **TemplatesDir,** che è *%TEMPLATE_PATH% \\ &lt; SomeProjectItems, &gt;* è il nodo a sinistra dell'albero della finestra di dialogo **Aggiungi** nuovo elemento. Gli elementi aggiuntivi nell'albero si basano sulla sottodirectory all'interno di tale directory radice. I file disponibili per l'aggiunta al progetto sono gli elementi nel riquadro destro della **finestra di** dialogo Aggiungi nuovo elemento.

 In genere, questa cartella conterrà i file modello per il progetto, ad esempio un file HTML o *CPP* modello, ed eventuali file con estensione *vsz* per l'avvio delle procedure guidate. Per controllare la modalità di visualizzazione degli elementi, è anche possibile includere file con estensione *vsdir* per la localizzazione di icone e nomi di directory. La stringa localizzata è la didascalia visualizzata nella finestra di dialogo che rappresenta questo nodo **nell'albero** della finestra di dialogo Aggiungi nuovo elemento .

 Tuttavia, non è necessario avere tutti gli elementi in un unico file *con estensione vsdir.* È possibile avere un file *con estensione vsdir* per ogni elemento nella directory . Per altre informazioni, vedere [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) e File di [descrizione della directory modello (con estensione vsdir).](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

> [!NOTE]
> I *file con estensione vsdir* nelle directory dei modelli sono facoltativi. Se si vuole semplicemente inserire un elemento di progetto  nella directory e visualizzarlo nella finestra di dialogo Aggiungi nuovo elemento, è possibile inserire tale file nella directory templates specificata nell'istruzione **TemplatesDir.** Il file verrà quindi visualizzato nel riquadro destro della finestra di dialogo Aggiungi nuovo **elemento** per il progetto. Tuttavia, se si vuole visualizzare una didascalia localizzata per il file o un'icona, è necessario includere almeno un file con estensione *vsdir* nella directory templates.

## <a name="group-project-items"></a>Raggruppare gli elementi del progetto
 Se si desidera contenere gruppi  di modelli in cartelle nell'albero della finestra di dialogo Aggiungi nuovo elemento, è necessario disporre di sottodirectory nella directory del modello radice con gli elementi in essi contenuti. Quando viene **visualizzata la finestra di** dialogo Aggiungi nuovo elemento, gli utenti visualizzano anche le sottocartelle e potranno selezionare gli elementi del progetto da tali sottocartelle.

 La priorità di ordinamento nel segmento di codice determina dove verrà creata la directory del modello nell'albero rispetto ad altri elementi del nodo della struttura ad albero. Per la **finestra di dialogo** Aggiungi nuovo elemento, la priorità di ordinamento è tutto ciò che è necessario includere in modo che gli elementi verranno visualizzati nella posizione corretta nella finestra di dialogo.

 È anche possibile implementare l'interfaccia per filtrare gli elementi visualizzati nella finestra di dialogo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Aggiungi nuovo elemento .  Implementando questa interfaccia, è possibile configurare una directory modello su disco che contiene, ad esempio, 50 file di modello e di procedura guidata. In questo modo, è possibile avere tipi di progetto diversi con 20 file che appartengono a un tipo di progetto, gli altri 30 file che appartengono a un altro tipo di progetto e tutti i file disponibili in un tipo generale di progetto. In questo modo, a seconda del modello di progetto creato, è possibile visualizzare un set diverso di file modello.

 In un progetto Visual Basic, ad esempio, potrebbero essere presenti progetti Web e progetti client. I Web Form non sono elementi utili da aggiungere a un progetto client e i Windows Form non sono elementi utili da aggiungere a un progetto server Web. Pertanto, è possibile creare una directory modello che contiene tutti i file per entrambi i tipi di progetto. Implementando è quindi possibile nascondere gli elementi che non devono essere visualizzati in base al tipo di progetto o alle impostazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> del progetto nel progetto.

## <a name="filter-project-items"></a>Filtrare gli elementi del progetto
 `IVsFilterAddProjectItemDlg2` fornisce per filtrare gli elementi nell'albero (riquadro sinistro) e i file di progetto (riquadro destro) nei modi seguenti:

- In base ai nomi localizzati (didascalie visualizzate nella finestra di dialogo contenuta nel file con estensione *vsdir)* forniti da `IVsFilterAddProjectItemDlg` .

- In base ai nomi effettivi dei file e delle cartelle su disco (non localizzati, nessun file con estensione *vsdir)* forniti da `IVsFilterAddProjectItemDlg` .

- Per categoria, fornita da `IVsFilterAddProjectItemDlg2` .

  Per filtrare in base alla categoria, fornire una stringa di categoria a un elemento nel file con estensione *vsdir,* ad esempio *Web Form* o *Elemento client* in Visual Basic. Il codice della finestra di dialogo recupera quindi la classificazione di categoria dal file con estensione *vsdir* e la passa all'utente. È quindi possibile passare queste informazioni all'implementazione di per filtrare la finestra di dialogo Aggiungi `IVsFilterAddProjectItemDlg2` nuovo elemento in base alle categorie.  È anche possibile filtrare gli elementi per le pagine Web o come casi dell'applicazione Win32 client. Inoltre, è possibile identificare gli elementi contrassegnati [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] come Microsoft Foundation Classes (MFC) o atl (Active Template Library). Quando si identificano questi elementi, il sistema del progetto può definire le proprie classificazioni in modo che il sistema possa essere filtrato in base a categorie e classificazioni.

  Se si implementa questa funzionalità di filtro, non è necessario eseguire il mapping di una tabella di ogni elemento che deve essere nascosto. È sufficiente classificare gli elementi in tipi e inserire le classificazioni nel file o nei file con estensione *vsdir.* È quindi possibile nascondere qualsiasi elemento con una classificazione specifica implementando l'interfaccia . In questo modo, è possibile rendere dinamici gli elementi nella **finestra** di dialogo Aggiungi nuovo elemento in base allo stato all'interno del progetto.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registrare modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATID per oggetti usati in genere per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Aggiungere modelli di progetto e di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [File di descrizione della directory del modello (con estensione vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
