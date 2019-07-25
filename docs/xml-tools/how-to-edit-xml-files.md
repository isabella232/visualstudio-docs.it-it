---
title: 'Procedura: di file XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1bcc560c1e0cabd222da68e98de18d7b8bef6ec6
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483401"
---
# <a name="how-to-edit-xml-files"></a>Procedura: Modificare i file XML

L'editor XML è il nuovo editor per i file XML. Può essere usato per un file XML autonomo o per un file associato a un progetto Visual Studio. L'editor XML è associato alle estensioni di file seguenti: *. config*, *. DTD*, *. XML*, *. xsd*, *. XDR*, *. xsl*, *. XSLT*e *. vssettings*. L'editor XML è associato anche a qualsiasi altro tipo di file che non dispone di un editor specifico registrato e che contiene contenuto XML o DTD.

> [!NOTE]
> I documenti XHTML sono gestiti dall'editor HTML.

Per modificare un file XML, fare doppio clic sul file che si desidera modificare.

## <a name="add-a-new-xml-file-to-a-project"></a>Aggiungere un nuovo file XML a un progetto

1. Scegliere **Aggiungi nuovo elemento**dal menu **progetto** .

2. Selezionare **file XML** dal riquadro **modelli** .

3. Immettere il nome del file nel campo **nome** e fare clic su **Aggiungi**.

   Il file XML viene aggiunto al progetto e aperto nell'editor XML. Il file contiene la dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Aggiungere un file XML esistente a un progetto

1. Scegliere **Aggiungi elemento esistente**dal menu **progetto** .

   Verrà visualizzata la finestra di dialogo **Aggiungi elemento esistente** .

2. Selezionare un file XML e premere **Aggiungi**.

## <a name="create-a-new-xml-or-xslt-file"></a>Creazione di un nuovo file XML o XSLT

1. Scegliere **nuovo**dal menu **file** .

   Verrà visualizzata la finestra di dialogo **nuovo file** .

2. Selezionare il **file XML** per creare un nuovo file XML. in alternativa, selezionare **file XSLT** per creare un nuovo foglio di stile XSLT.

3. Fare clic su **Apri**.

## <a name="create-an-empty-project-for-xml-files"></a>Creare un progetto vuoto per i file XML

::: moniker range="vs-2017"

1. Scegliere **nuovo** > **progetto**dal menu **file** .

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Selezionare il linguaggio del codice desiderato e quindi selezionare il modello di **progetto vuoto (.NET Framework)** .

3. Fare clic su **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Scegliere **nuovo** > **progetto**dal menu **file** .

2. Immettere **progetto vuoto** nella casella di ricerca del modello, selezionare il modello di **progetto vuoto (.NET Framework)** , quindi fare clic su **Avanti**.

3. Fare clic su **Create**(Crea).

::: moniker-end

4. Aggiunta di file XML al progetto.

   L'editor XML consente di trovare gli schemi aggiunti al progetto e di utilizzarli per la convalida e IntelliSense in qualsiasi file XML, schema o XSLT modificato durante l'apertura del progetto.

## <a name="see-also"></a>Vedere anche

- [Editor XML](../xml-tools/xml-editor.md)
- [Proprietà del documento XML, finestra Proprietà](../xml-tools/xml-document-properties-properties-window.md)
- [Procedura: Creazione di un XML Schema da un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)