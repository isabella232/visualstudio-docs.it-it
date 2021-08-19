---
title: Raccolte private | Microsoft Docs
description: Informazioni su come condividere i controlli, i modelli e gli strumenti che si sviluppano in Visual Studio SDK pubblicandoli in una raccolta privata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ae9a2683cf7f80b415b81a2f3f96d940ff62dc99
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102142"
---
# <a name="private-galleries"></a>Raccolte private
È possibile condividere i controlli, i modelli e gli  strumenti che si sviluppano pubblicandoli in una raccolta privata sulla Intranet per l'organizzazione, come indicato di seguito:

- Creare un feed Atom (RSS) in una posizione centrale (repository) adeguatamente configurata nella intranet. Per altre informazioni, [vedere Procedura: Creare un feed Atom per una raccolta privata.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

- Distribuire un file *con estensione pkgdef* che descrive la raccolta privata. È consigliabile usare questa configurazione per gli amministratori che vogliono connettere una raccolta privata a più computer contemporaneamente.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Aggiungere una raccolta privata alle estensioni e agli aggiornamenti in Visual Studio
 Quando è disponibile una raccolta privata, è possibile aggiungerla a **Estensioni** e aggiornamenti in Visual Studio.

 ![Finestra di dialogo Aggiungi di Gestione estensioni](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Per aggiungere una raccolta privata a Estensioni e aggiornamenti

1. Sulla barra dei menu scegliere **Strumenti**  >  **Opzioni**.

2. Nel nodo **Ambiente** selezionare **Estensioni e aggiornamenti.**

3. Fare clic sul pulsante **Aggiungi**.

4. Nel campo **Nome** immettere un nome per la raccolta privata, ad esempio `My Gallery` .

5. Nel campo **URL** immettere l'URL del feed Atom o del SharePoint che ospita la raccolta privata.

    1. Se l'host è un feed Atom che si connette alla raccolta privata, l'URL sarà simile al seguente: `http://www.mywebsite/mygallery/atom.xml` .  Questo URL può fare riferimento a un file o a un percorso di rete.

    2. Se l'host è un SharePoint, l'URL sarà simile al seguente: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Gestire raccolte private
 Un amministratore può rendere disponibile una raccolta privata a più computer contemporaneamente modificando il Registro di sistema in ogni computer. A tale scopo, creare un file *con estensione pkgdef* che descrive le nuove chiavi del Registro di sistema e i relativi valori.  Il formato di questo file è il seguente.

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

 Per altre informazioni, vedere Procedura: Gestire una raccolta privata usando le [impostazioni del Registro di sistema.](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)

## <a name="install-extensions-from-a-private-gallery"></a>Installare le estensioni da una raccolta privata
 È possibile cercare e installare Visual Studio da una raccolta privata in **Estensioni e aggiornamenti.** La procedura seguente usa una raccolta privata denominata `My Gallery` .

 ![Installazione della galleria privata di Gestione estensioni](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Per cercare e installare estensioni da una raccolta privata

1. Sulla barra dei menu scegliere **Strumenti**  >  **Estensioni e aggiornamenti.**

2. Nel riquadro sinistro selezionare **Estensioni online** e quindi **Selezionare Raccolta.**

3. Nel riquadro destro selezionare un'estensione e quindi scegliere il **pulsante Scarica.**

## <a name="update-extensions-from-a-private-gallery"></a>Aggiornare le estensioni da una raccolta privata
 Quando nella raccolta privata vengono Visual Studio nuove versioni delle estensioni, è possibile aggiornare le estensioni installate. La procedura seguente usa una raccolta privata denominata `My Repository` .

 ![Aggiornamento della galleria privata di Gestione estensioni](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Per aggiornare un'estensione installata da una raccolta privata

1. Sulla barra dei menu scegliere **Strumenti**  >  **Estensioni e aggiornamenti.**

2. Nel riquadro sinistro selezionare **Aggiornamenti** e quindi **Selezionare Repository.**

3. Nel riquadro destro selezionare un'estensione e quindi scegliere il **pulsante** Aggiorna.

## <a name="see-also"></a>Vedi anche
- [Individuare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Spedire Visual Studio estensioni](../extensibility/shipping-visual-studio-extensions.md)
