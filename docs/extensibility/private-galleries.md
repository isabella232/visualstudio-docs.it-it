---
title: Gallerie Private Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: afd1d79d7f1846e60386d2a9478466bf7eae72e4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444648"
---
# <a name="private-galleries"></a>Gallerie private
È possibile condividere i controlli, i modelli e gli strumenti sviluppati pubblicandoli in una *raccolta privata* della rete Intranet dell'organizzazione, come indicato di seguito:

- Creare un feed Atom (RSS) in una posizione centrale (repository) opportunamente configurata nella rete Intranet. Per ulteriori informazioni, vedere [Procedura: creare un feed Atom per una raccolta privata.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

- Distribuire un file *con estensione pkgdef* che descrive la raccolta privata. Questa configurazione è consigliata per gli amministratori che desiderano connettere una raccolta privata a più computer contemporaneamente.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Aggiungere una raccolta privata alle estensioni e agli aggiornamenti in Visual StudioAdd a private gallery to extensions and updates in Visual Studio
 Quando è disponibile una raccolta privata, è possibile aggiungerla a **estensioni e aggiornamenti** in Visual Studio.When a private gallery is available, you can add it to Extensions and Updates in Visual Studio.

 ![Finestra di dialogo Aggiungi di Gestione estensioni](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Per aggiungere una raccolta privata a Estensioni e aggiornamenti

1. Nella barra dei menu scegliere**Opzioni** **degli strumenti** > .

2. Nel nodo **Ambiente** selezionare **Estensioni e aggiornamenti**.

3. Fare clic sul pulsante **Aggiungi**.

4. Nel campo **Nome** immettere un nome per la `My Gallery`raccolta privata, ad esempio .

5. Nel campo **URL** immettere l'URL del feed Atom o del sito di SharePoint che ospita la raccolta privata.

    1. Se l'host è un feed Atom che si connette alla `http://www.mywebsite/mygallery/atom.xml`raccolta privata, l'URL sarà simile al seguente: .  Questo URL può fare riferimento a un file o a un percorso di rete.

    2. Se l'host è un sito di SharePoint, l'URL sarà simile al seguente: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`.

### <a name="manage-private-galleries"></a>Gestire gallerie private
 Un amministratore può rendere disponibile una raccolta privata a più computer contemporaneamente modificando il Registro di sistema in ogni computer. A tale scopo, creare un file *con estensione pkgdef* che descrive le nuove chiavi del Registro di sistema e i relativi valori.  Il formato di questo file è il seguente.

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

 Per ulteriori informazioni, vedere [Procedura: gestire una raccolta privata utilizzando le impostazioni del Registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)di sistema .

## <a name="install-extensions-from-a-private-gallery"></a>Installare le estensioni da una raccolta privata
 È possibile cercare e installare le estensioni di Visual Studio da una raccolta privata in **Estensioni e aggiornamenti**. La procedura seguente utilizza `My Gallery`una raccolta privata denominata .

 ![Installazione della galleria privata di Gestione estensioni](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Per cercare e installare estensioni da una raccolta privata

1. Nella barra dei menu scegliere**Estensioni e aggiornamenti**degli **strumenti** > .

2. Nel riquadro sinistro selezionare **Estensioni in linea**, quindi **Raccolta personale**.

3. Nel riquadro destro selezionare un'estensione, quindi scegliere il pulsante **Download.**

## <a name="update-extensions-from-a-private-gallery"></a>Aggiornare le estensioni da una raccolta privataUpdate extensions from a private gallery
 Man mano che le nuove versioni delle estensioni di Visual Studio vengono pubblicate nella raccolta privata, è possibile aggiornare le estensioni installate. La procedura seguente utilizza `My Repository`una raccolta privata denominata .

 ![Aggiornamento della galleria privata di Gestione estensioni](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Per aggiornare un'estensione installata da una raccolta privataTo update an installed extension from a private gallery

1. Nella barra dei menu scegliere**Estensioni e aggiornamenti**degli **strumenti** > .

2. Nel riquadro sinistro selezionare **Aggiornamenti**e quindi **Repository personali**.

3. Nel riquadro destro selezionare un'estensione, quindi scegliere il pulsante **Aggiorna.In** the right pane, select an extension, and then choose the Update button.

## <a name="see-also"></a>Vedere anche
- [Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Spedire le estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
