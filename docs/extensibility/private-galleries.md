---
title: Raccolte private | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027181d16024964d5487be2b3eb0b4ca261f98e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433586"
---
# <a name="private-galleries"></a>Raccolte private
È possibile condividere i controlli, modelli e strumenti che si sviluppano inviando messaggi a un *raccolta privata* nella intranet per l'organizzazione, come indicato di seguito:

- Creare un atomo (feed RSS) in una posizione centrale opportunamente configurata (repository) nella intranet. Per altre informazioni, vedere [Procedura: Creare un feed Atom per una raccolta privata](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Distribuire un' *pkgdef* file che descrive la raccolta privata. Si consiglia questa configurazione per gli amministratori che desiderano connettersi una raccolta privata a più computer contemporaneamente.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Aggiungere una raccolta privata a estensioni e aggiornamenti in Visual Studio
 Quando una raccolta privata è disponibile, è possibile aggiungerla alla **estensioni e aggiornamenti** in Visual Studio.

 ![Finestra di dialogo Aggiungi Gestione estensioni](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Per aggiungere una raccolta privata a estensioni e aggiornamenti

1. Nella barra dei menu scegliere **Strumenti** > **Opzioni**.

2. Nel **ambiente** nodo, seleziona **estensioni e aggiornamenti**.

3. Scegliere il pulsante **Aggiungi**.

4. Nel **Name** immettere un nome per la raccolta privata, ad esempio, `My Gallery`.

5. Nel **URL** immettere l'URL del feed Atom o sito di SharePoint che ospita la raccolta privata.

    1. Se l'host è un feed Atom che si connette alla raccolta privata, l'URL sarà simile a quella: http://www.mywebsite/mygallery/atom.xml.  Questo URL può fare riferimento a un file o un percorso di rete.

    2. Se l'host è un sito di SharePoint, l'URL sarebbe simile a questo: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.

### <a name="manage-private-galleries"></a>Gestire raccolte private
 Un amministratore può renderla una raccolta privata disponibile per diversi computer nello stesso momento modificando il Registro di sistema in ogni computer. A questo scopo, creare un *pkgdef* file che descrive le nuove chiavi del Registro di sistema e i relativi valori.  Il formato di questo file è come indicato di seguito.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Per altre informazioni, vedere [Procedura: Gestire una raccolta privata mediante le impostazioni del Registro di sistema](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Installare le estensioni da una raccolta privata
 È possibile cercare e installare le estensioni di Visual Studio da una raccolta privata in **estensioni e aggiornamenti**. La procedura seguente usa una raccolta privata denominata `My Gallery`.

 ![Gestore estensioni del installazione raccolta privata](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Per cercare e installare le estensioni da una raccolta privata

1. Nella barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.

2. Nel riquadro sinistro, selezionare **estensioni Online**, quindi selezionare **raccolta personale**.

3. Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **scaricare** pulsante.

## <a name="update-extensions-from-a-private-gallery"></a>Aggiornare le estensioni da una raccolta privata
 Come le nuove versioni delle estensioni di Visual Studio vengono registrate nella raccolta privata, è possibile aggiornare le estensioni installate. La procedura seguente usa una raccolta privata denominata `My Repository`.

 ![Aggiornamento della Galleria privata di Gestione estensioni](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Per aggiornare un'estensione installata da una raccolta privata

1. Nella barra dei menu, scegliere **degli strumenti** > **estensioni e aggiornamenti**.

2. Nel riquadro sinistro, selezionare **aggiornamenti**, quindi selezionare **Repository personale**.

3. Nel riquadro di destra, selezionare un'estensione e quindi scegliere il **Update** pulsante.

## <a name="see-also"></a>Vedere anche
- [Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Fornire estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)