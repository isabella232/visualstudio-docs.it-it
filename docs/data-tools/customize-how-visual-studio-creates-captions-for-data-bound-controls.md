---
title: Personalizzare le didascalie per controlli con associazione a dati
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1745aef29da9fc8efd49789f0112c903128f6f74
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567585"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati

Quando si trascinano elementi dal [finestra Origini dati](add-new-data-sources.md#data-sources-window) in una finestra di progettazione, entra in gioco una particolare attenzione: i nomi delle colonne nelle etichette della didascalia vengono riformattati in una stringa più leggibile quando due o più parole sono state trovate per essere concatenati tra loro.

::: moniker range="vs-2017"

È possibile personalizzare il modo in cui vengono create queste etichette impostando il **SmartCaptionExpression**, **SmartCaptionReplacement**, e **SmartCaptionSuffix** valori in il **progettisti HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data** chiave del Registro di sistema.

::: moniker-end

::: moniker range=">=vs-2019"

È possibile personalizzare il modo in cui vengono create queste etichette impostando il **SmartCaptionExpression**, **SmartCaptionReplacement**, e **SmartCaptionSuffix** valori in il **progettisti HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data** chiave del Registro di sistema.

::: moniker-end

> [!NOTE]
> Questa chiave del Registro di sistema non esiste fino a quando non si crea.

I sottotitoli intelligente è controllato dall'espressione regolare immessa nel valore del **SmartCaptionExpression** valore. Aggiunta il **progettazione visiva di dati** chiave del Registro di sistema esegue l'override dell'espressione regolare predefinita che controlla le etichette della didascalia. Per altre informazioni sulle espressioni regolari, vedere [usando le espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

La tabella seguente descrive i valori del Registro di sistema che controllano le etichette della didascalia.

|Elemento Registro di sistema|Descrizione|
|-------------------|-----------------|
|**SmartCaptionExpression**|L'espressione regolare che è utilizzare in modo che corrispondano ai modelli.|
|**SmartCaptionReplacement**|Il formato per visualizzare tutti i gruppi di una corrispondenza con il **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Stringa facoltativa da aggiungere alla fine della didascalia.|

La tabella seguente elenca le impostazioni predefinite interne per questi valori del Registro di sistema.

|Elemento Registro di sistema|Valore predefinito|Descrizione|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll})(\\\p{Lu})&#124;_+**|Corrisponde a una lettera minuscola seguita da una lettera maiuscola o un carattere di sottolineatura.|
|**SmartCaptionReplacement**|**$1 $2**|Il **1 dollaro** rappresenta tutti i caratteri corrispondenti nella prima delle parentesi dell'espressione e il **$2** rappresenta tutti i caratteri parentesi secondo una corrispondenza. La sostituzione è la prima corrispondenza, uno spazio e quindi la seconda corrispondenza.|
|**SmartCaptionSuffix**|**:**|Rappresenta un carattere aggiunto alla stringa restituita. Ad esempio, se la didascalia è `Company Name`, rende il suffisso `Company Name:`|

> [!CAUTION]
> Prestare molta attenzione quando si esegue alcuna operazione nell'Editor del Registro di sistema. Eseguire il backup del Registro di sistema prima di modificarlo. Se si usa l'Editor del Registro di sistema in modo non corretto, si possono causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che sia possono risolvere i problemi derivanti utilizzando l'Editor del Registro di sistema in modo non corretto. L'utilizzo dell'editor del Registro di sistema è a rischio dell'utente.
>
> Per informazioni sul backup, la modifica e il ripristino di registro di sistema, vedere [le informazioni del Registro di sistema di Windows per gli utenti avanzati](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modificare il comportamento di sottotitoli codificato intelligente della finestra Origini dati

1. Aprire una finestra di comando facendo **avviare** e quindi **eseguire**.

2. Tipo di `regedit` nella **eseguire** nella finestra di dialogo e fare clic su **OK**.

3. Espandere la **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio**nodo.

::: moniker range="vs-2017"

4. Fare doppio clic il **15.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Fare doppio clic il **16.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.

::: moniker-end

5. Fare doppio clic il **progettazione visiva di dati** nodo e creare tre nuovi valori di stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Fare doppio clic il **SmartCaptionExpression** valore, quindi selezionare **Modify**.

7. Immettere l'espressione regolare desidera che il **Zdroje dat** finestra da utilizzare.

8. Fare doppio clic il **SmartCaptionReplacement** valore, quindi selezionare **Modify**.

9. Immettere la sostituzione stringa formattati nel modo desiderato visualizzare i modelli di corrispondenza nell'espressione regolare.

10. Fare doppio clic il **SmartCaptionSuffix** valore, quindi selezionare **Modify**.

11. Immettere eventuali caratteri che si desidera venga visualizzato alla fine della didascalia.

    La volta successiva che si trascinano elementi dal **Zdroje dat** finestra, le etichette della didascalia vengono create utilizzando i nuovi valori del Registro di sistema specificati.

## <a name="turn-off-the-smart-captioning-feature"></a>Disattivare la funzionalità smart i sottotitoli codificata

1. Aprire una finestra di comando facendo **avviare** e quindi **eseguire**.

2. Tipo di `regedit` nella **eseguire** nella finestra di dialogo e fare clic su **OK**.

3. Espandere la **HKEY_CURRENT_USER** > **Software** > **Microsoft** > **VisualStudio**nodo.

::: moniker range="vs-2017"

4. Fare doppio clic il **15.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.

::: moniker-end

::: moniker range=">=vs-2019"

4. Fare doppio clic il **16.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.

::: moniker-end

5. Fare doppio clic il **progettazione visiva di dati** nodo e creare tre nuovi valori di stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Fare doppio clic il **SmartCaptionExpression** e selezionare **Modify**.

7. Immettere `(.*)` per il valore. Ciò corrisponderà alla stringa intera.

8. Fare doppio clic il **SmartCaptionReplacement** e selezionare **Modify**.

9. Immettere `$1` per il valore. Ciò sostituisce la stringa con il valore corrispondente, ovvero l'intera stringa in modo che rimarrà invariata.

    La volta successiva che si trascinano elementi dal **Zdroje dat** finestra, le etichette della didascalia vengono create con sottotitoli in lingua originale non modificate.

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)