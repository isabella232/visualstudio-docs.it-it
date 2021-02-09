---
title: Personalizzare le didascalie per i controlli associati a dati
description: Personalizzare il modo in cui Visual Studio crea le didascalie per i controlli associati a dati. Modificare il comportamento di didascalia intelligente della finestra Origini dati. Disattiva le didascalie intelligenti.
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: be9a6840c3b41b442e5019e08c4d2f4d2fa5c3dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858995"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati

Quando si trascinano elementi dalla [finestra Origini dati](add-new-data-sources.md#data-sources-window) in una finestra di progettazione, si verifica un particolare interesse: i nomi di colonna nelle etichette di didascalia vengono riformattati in una stringa più leggibile quando due o più parole sono concatenate insieme.

::: moniker range="vs-2017"

È possibile personalizzare la modalità di creazione di queste etichette impostando i valori **SmartCaptionExpression**, **SmartCaptionReplacement** e **SmartCaptionSuffix** nella chiave del registro di sistema **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designers** .

::: moniker-end

::: moniker range=">=vs-2019"

È possibile personalizzare la modalità di creazione di queste etichette impostando i valori **SmartCaptionExpression**, **SmartCaptionReplacement** e **SmartCaptionSuffix** nella chiave del registro di sistema **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data Designers** .

::: moniker-end

> [!NOTE]
> Questa chiave del registro di sistema non esiste fino a quando non viene creata.

La didascalia intelligente è controllata dall'espressione regolare immessa nel valore del valore **SmartCaptionExpression** . L'aggiunta della chiave del registro di sistema **Data Designer** sostituisce l'espressione regolare predefinita che controlla le etichette delle didascalie. Per altre informazioni sulle espressioni regolari, vedere [uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

La tabella seguente descrive i valori del registro di sistema che controllano le etichette delle didascalie.

|Elemento del registro di sistema|Descrizione|
|-------------------|-----------------|
|**SmartCaptionExpression**|Espressione regolare usata per trovare la corrispondenza con i modelli.|
|**SmartCaptionReplacement**|Formato per visualizzare i gruppi corrispondenti in **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Stringa facoltativa da aggiungere alla fine della didascalia.|

Nella tabella seguente sono elencate le impostazioni predefinite interne per questi valori del registro di sistema.

|Elemento del registro di sistema|Valore predefinito|Spiegazione|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**( \\ \p{ll}) ( \\ \p{Lu}) &#124;_ +**|Corrisponde a un carattere minuscolo seguito da un carattere maiuscolo o un carattere di sottolineatura.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** rappresenta tutti i caratteri corrispondenti nelle prime parentesi dell'espressione e il **$2** rappresenta tutti i caratteri corrispondenti nella seconda parentesi. La sostituzione è la prima corrispondenza, uno spazio e quindi la seconda corrispondenza.|
|**SmartCaptionSuffix**|**:**|Rappresenta un carattere aggiunto alla stringa restituita. Ad esempio, se la didascalia è `Company Name` , il suffisso lo rende `Company Name:`|

> [!CAUTION]
> Prestare attenzione quando si esegue qualsiasi operazione nell'editor del registro di sistema. Eseguire il backup del registro di sistema prima di modificarlo. Se si utilizza l'editor del registro di sistema in modo errato, è possibile che si verifichino gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che i problemi causati dall'utilizzo errato dell'editor del registro di sistema possano essere risolti. L'uso dell'editor del Registro di sistema è di sola responsabilità dell'utente.
>
> Per informazioni sul backup, la modifica e il ripristino del registro di sistema, vedere [informazioni del registro di sistema di Windows per gli utenti avanzati](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users).

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modificare il comportamento della didascalia intelligente della finestra Origini dati

1. Aprire una finestra di comando facendo clic su **Start** , quindi su **Esegui**.

2. Digitare `regedit` nella finestra di dialogo **Esegui** , quindi fare clic su **OK**.

3. Espandere il **HKEY_CURRENT_USER**  >  nodo **software**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Fare clic con il pulsante destro del mouse sul nodo **15,0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Fare clic con il pulsante destro del mouse sul nodo **16,0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

5. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare tre nuovi valori stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Fare clic con il pulsante destro del mouse sul valore **SmartCaptionExpression** e scegliere **modifica**.

7. Immettere l'espressione regolare che si desidera venga utilizzata dalla finestra **origini dati** .

8. Fare clic con il pulsante destro del mouse sul valore **SmartCaptionReplacement** e scegliere **modifica**.

9. Immettere la stringa di sostituzione formattata nel modo in cui si desidera visualizzare i modelli corrispondenti nell'espressione regolare.

10. Fare clic con il pulsante destro del mouse sul valore **SmartCaptionSuffix** e scegliere **modifica**.

11. Immettere i caratteri che si desidera visualizzare alla fine della didascalia.

    La volta successiva che si trascinano gli elementi dalla finestra **origini dati** , le etichette didascalia vengono create utilizzando i nuovi valori del registro di sistema specificati.

## <a name="turn-off-the-smart-captioning-feature"></a>Disattivare la funzionalità di Smart Caption

1. Aprire una finestra di comando facendo clic su **Start** , quindi su **Esegui**.

2. Digitare `regedit` nella finestra di dialogo **Esegui** , quindi fare clic su **OK**.

3. Espandere il **HKEY_CURRENT_USER**  >  nodo **software**  >  **Microsoft**  >  **VisualStudio** .

::: moniker range="vs-2017"

4. Fare clic con il pulsante destro del mouse sul nodo **15,0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Fare clic con il pulsante destro del mouse sul nodo **16,0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

5. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare tre nuovi valori stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionExpression** e scegliere **modifica**.

7. Immettere `(.*)` per il valore. Corrisponderà all'intera stringa.

8. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionReplacement** e scegliere **modifica**.

9. Immettere `$1` per il valore. Questa operazione sostituisce la stringa con il valore corrispondente, ovvero l'intera stringa in modo che rimanga invariata.

    La volta successiva che si trascinano gli elementi dalla finestra **origini dati** , le etichette didascalia vengono create con didascalie non modificate.

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
