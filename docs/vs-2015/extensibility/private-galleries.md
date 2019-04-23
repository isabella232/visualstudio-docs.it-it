---
title: Raccolte private | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 097d666a839f67e657610b34641ed29da91797be
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085857"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile condividere i controlli, modelli e strumenti che si sviluppano inviando messaggi a un *raccolta privata* nella intranet per l'organizzazione, come indicato di seguito:  
  
- Creare un atomo (feed RSS) in una posizione centrale opportunamente configurata (repository) nella intranet. Per altre informazioni, vedere [Procedura: Creare un Atom per una raccolta privata di Feed](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
- Distribuire un file. pkgdef che descrive la raccolta privata. Si consiglia questa configurazione per gli amministratori che desiderano connettersi una raccolta privata a più computer contemporaneamente.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Aggiunta di una raccolta privata a estensioni e aggiornamenti in Visual Studio  
 Quando una raccolta privata è disponibile, è possibile aggiungerla alla **estensioni e aggiornamenti** in Visual Studio.  
  
 ![Finestra di dialogo Aggiungi Gestione estensioni](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Per aggiungere una raccolta privata a estensioni e aggiornamenti  
  
1. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.  
  
2. Nel **ambiente** nodo, seleziona **estensioni e aggiornamenti**.  
  
3. Scegliere il pulsante **Aggiungi**.  
  
4. Nel **Name** immettere un nome per la raccolta privata, ad esempio, `My Gallery`.  
  
5. Nel **URL** immettere l'URL del feed Atom o sito di SharePoint che ospita la raccolta privata.  
  
    1. Se l'host è un feed Atom che si connette alla raccolta privata, l'URL sarà simile a quella: http://www.mywebsite/mygallery/atom.xml.  Questo URL può fare riferimento a un file o un percorso di rete.  
  
    2. Se l'host è un sito di SharePoint, l'URL sarebbe simile a questo: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.  
  
### <a name="managing-private-galleries"></a>La gestione di raccolte Private  
 Un amministratore può renderla una raccolta privata disponibile per diversi computer nello stesso momento modificando il Registro di sistema in ogni computer. A tale scopo, creare un file. pkgdef che descrive le nuove chiavi del Registro di sistema e i relativi valori.  Il formato di questo file è come indicato di seguito.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Per altre informazioni, vedere [Procedura: Gestire una raccolta privata mediante le impostazioni del Registro di sistema](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Installazione di estensioni di una raccolta privata  
 È possibile cercare e installare le estensioni di Visual Studio da una raccolta privata in **estensioni e aggiornamenti**. La procedura seguente usa una raccolta privata denominata `My Gallery`.  
  
 ![Gestore estensioni del installazione raccolta privata](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Per cercare e installare le estensioni da una raccolta privata  
  
1. Nella barra dei menu scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
2. Nel riquadro sinistro, selezionare **estensioni Online**, quindi selezionare **raccolta personale**.  
  
3. Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **scaricare** pulsante.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Aggiornamento delle estensioni da una raccolta privata  
 Come le nuove versioni delle estensioni di Visual Studio vengono registrate nella raccolta privata, è possibile aggiornare le estensioni installate. La procedura seguente usa una raccolta privata denominata `My Repository`.  
  
 ![Aggiornamento della Galleria privata di Gestione estensioni](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Per aggiornare un'estensione installata da una raccolta privata  
  
1. Nella barra dei menu scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
2. Nel riquadro sinistro, selezionare **aggiornamenti**, quindi selezionare **Repository personale**.  
  
3. Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **Update** pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e uso di estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Distribuzione delle estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
