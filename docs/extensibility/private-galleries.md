---
title: Raccolte private | Microsoft Docs
description: Informazioni su come condividere i controlli, i modelli e gli strumenti sviluppati in Visual Studio SDK, inserendoli in una raccolta privata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5b58c5885f4fc9bd3765c818ea414bee0dbf3c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961859"
---
# <a name="private-galleries"></a>Raccolte private
È possibile condividere i controlli, i modelli e gli strumenti sviluppati inserendoli in una *raccolta privata* della Intranet per l'organizzazione, come indicato di seguito:

- Creare un feed Atom (RSS) in una posizione centrale opportunamente configurata (repository) nella Intranet. Per altre informazioni, vedere [procedura: creare un feed Atom per una raccolta privata](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Distribuire un file con *estensione pkgdef* che descrive la raccolta privata. Si consiglia di eseguire questa configurazione per gli amministratori che desiderano connettere una raccolta privata a molti computer nello stesso momento.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Aggiungere una raccolta privata a estensioni e aggiornamenti in Visual Studio
 Quando è disponibile una raccolta privata, è possibile aggiungerla a **estensioni e aggiornamenti** in Visual Studio.

 ![Finestra di dialogo Aggiungi di Gestione estensioni](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Per aggiungere una raccolta privata a estensioni e aggiornamenti

1. Sulla barra dei menu scegliere **strumenti**  >  **Opzioni**.

2. Nel nodo **ambiente** selezionare **estensioni e aggiornamenti**.

3. Fare clic sul pulsante **Aggiungi**.

4. Nel campo **nome** immettere un nome per la raccolta privata, ad esempio `My Gallery` .

5. Nel campo **URL** immettere l'URL del feed Atom o del sito di SharePoint che ospita la raccolta privata.

    1. Se l'host è un feed Atom che si connette alla raccolta privata, l'URL sarà simile a quello riportato di seguito: `http://www.mywebsite/mygallery/atom.xml` .  Questo URL può fare riferimento a un file o a un percorso di rete.

    2. Se l'host è un sito di SharePoint, l'URL sarà simile a quello riportato di seguito: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Gestire le raccolte private
 Un amministratore può rendere una raccolta privata disponibile per più computer allo stesso tempo modificando il registro di sistema in ogni computer. A tale scopo, creare un file con *estensione pkgdef* che descriva le nuove chiavi del registro di sistema e i relativi valori.  Il formato di questo file è il seguente.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Per ulteriori informazioni, vedere [procedura: gestire una raccolta privata utilizzando le impostazioni del registro di sistema](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Installare le estensioni da una raccolta privata
 È possibile cercare e installare le estensioni di Visual Studio da una raccolta privata in **estensioni e aggiornamenti**. I passaggi seguenti usano una raccolta privata denominata `My Gallery` .

 ![Installazione della galleria privata di Gestione estensioni](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Per cercare e installare le estensioni da una raccolta privata

1. Sulla barra dei menu scegliere **strumenti**  >  **estensioni e aggiornamenti**.

2. Nel riquadro sinistro selezionare **estensioni online**, quindi selezionare **raccolta personale**.

3. Nel riquadro destro selezionare un'estensione e quindi fare clic sul pulsante **download** .

## <a name="update-extensions-from-a-private-gallery"></a>Aggiornare le estensioni da una raccolta privata
 Quando le nuove versioni delle estensioni di Visual Studio vengono pubblicate nella raccolta privata, è possibile aggiornare le estensioni installate. I passaggi seguenti usano una raccolta privata denominata `My Repository` .

 ![Aggiornamento della galleria privata di Gestione estensioni](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Per aggiornare un'estensione installata da una raccolta privata

1. Sulla barra dei menu scegliere **strumenti**  >  **estensioni e aggiornamenti**.

2. Nel riquadro sinistro selezionare **aggiornamenti**, quindi selezionare **repository personale**.

3. Nel riquadro destro selezionare un'estensione e quindi scegliere il pulsante **Aggiorna** .

## <a name="see-also"></a>Vedi anche
- [Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Distribuire le estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
