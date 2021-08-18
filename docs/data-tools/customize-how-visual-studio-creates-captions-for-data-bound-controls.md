---
title: Personalizzare le didascalie per i controlli associati a dati
description: Personalizzare la Visual Studio creare didascalie per i controlli associati a dati. Modificare il comportamento della didascalia intelligente della finestra Origini dati. Disattivare i sottotitoli intelligenti.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3a5979fda1e2fcbe8664df7171b1053acebb0506
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052811"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati

Quando si trascinano [](add-new-data-sources.md#data-sources-window) elementi dalla finestra Origini dati in una finestra di progettazione, entra in gioco una considerazione speciale: i nomi delle colonne nelle etichette della didascalia vengono riformattati in una stringa più leggibile quando due o più parole vengono concatenate.

::: moniker range="vs-2017"

È possibile personalizzare la modalità di creazione di queste etichette impostando i valori **SmartCaptionExpression**, **SmartCaptionReplacement** e **SmartCaptionSuffix** nella chiaveHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designersregistro di **sistema.**

::: moniker-end

::: moniker range=">=vs-2019"

È possibile personalizzare la modalità di creazione di queste etichette impostando i valori **SmartCaptionExpression**, **SmartCaptionReplacement** e **SmartCaptionSuffix** nella chiaveHKEY_CURRENT_USER\Software\Microsoft\VisualStudio\16.0\Data Designersregistro di **sistema.**

::: moniker-end

> [!NOTE]
> Questa chiave del Registro di sistema non esiste fino a quando non viene creata.

La didascalia intelligente è controllata dall'espressione regolare immessa nel valore **di SmartCaptionExpression.** L'aggiunta della chiave del Registro di sistema Data **Designers** sostituisce l'espressione regolare predefinita che controlla le etichette delle didascalie. Per altre informazioni sulle espressioni regolari, vedere [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Nella tabella seguente vengono descritti i valori del Registro di sistema che controllano le etichette delle didascalie.

|Elemento del Registro di sistema|Descrizione|
|-------------------|-----------------|
|**SmartCaptionExpression**|Espressione regolare utilizzata per trovare le corrispondenze con i criteri.|
|**SmartCaptionReplacement**|Formato per visualizzare tutti i gruppi corrispondenti in **SmartCaptionExpression.**|
|**SmartCaptionSuffix**|Stringa facoltativa da aggiungere alla fine della didascalia.|

Nella tabella seguente sono elencate le impostazioni predefinite interne per questi valori del Registro di sistema.

|Elemento del Registro di sistema|Valore predefinito|Spiegazione|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**( \\ \p{Ll})( \\ \p{Lu})&#124;_+**|Corrisponde a un carattere minuscolo seguito da un carattere maiuscolo o da un carattere di sottolineatura.|
|**SmartCaptionReplacement**|**$ 1 $ 2**|**$1** rappresenta tutti i caratteri corrispondenti nelle prime parentesi dell'espressione e **$2** rappresenta tutti i caratteri corrispondenti nelle seconde parentesi. La sostituzione è la prima corrispondenza, uno spazio e quindi la seconda corrispondenza.|
|**SmartCaptionSuffix**|**:**|Rappresenta un carattere aggiunto alla stringa restituita. Ad esempio, se la didascalia è `Company Name` , il suffisso la rende `Company Name:`|

> [!CAUTION]
> Prestare molta attenzione quando si esegue qualsiasi operazione nell'editor del Registro di sistema. Eseguire il backup del Registro di sistema prima di modificarlo. Se si usa l'editor del Registro di sistema in modo errato, è possibile che si possano verificare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che i problemi che si verificano usando l'editor del Registro di sistema possano essere risolti in modo non corretto. L'uso dell'editor del Registro di sistema è di sola responsabilità dell'utente.
>
> Per informazioni sul backup, la modifica e il ripristino del Registro di sistema, vedere l'Windows del Registro di [sistema per gli utenti avanzati.](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users)

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Modificare il comportamento dei sottotitoli intelligenti nella finestra Origini dati

1. Aprire una finestra di comando facendo clic **su Start** e quindi **su Esegui.**

2. Digitare `regedit` nella finestra di **dialogo** Esegui e fare clic su **OK.**

3. Espandere il **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio.**

::: moniker range="vs-2017"

4. Fare clic con il pulsante **destro del mouse sul nodo 15.0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Fare clic con il pulsante **destro del mouse sul nodo 16.0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

5. Fare clic con il pulsante **destro del mouse sul nodo Data Designers** (Finestre di progettazione dati) e creare tre nuovi valori stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Fare clic con il pulsante destro del mouse sul valore **SmartCaptionExpression** e **scegliere Modifica.**

7. Immettere l'espressione regolare che si **desidera utilizzare nella finestra Origini** dati.

8. Fare clic con il pulsante **destro del mouse sul valore SmartCaptionReplacement** e scegliere **Modifica.**

9. Immettere la stringa di sostituzione formattata nel modo in cui si vogliono visualizzare i criteri corrispondenti nell'espressione regolare.

10. Fare clic con il pulsante **destro del mouse sul valore SmartCaptionSuffix** e scegliere **Modifica.**

11. Immettere i caratteri da visualizzare alla fine della didascalia.

    La volta successiva che si trascinano elementi dalla **finestra Origini** dati, le etichette delle didascalie vengono create usando i nuovi valori del Registro di sistema forniti.

## <a name="turn-off-the-smart-captioning-feature"></a>Disattivare la funzionalità di sottotitoli in testo intelligente

1. Aprire una finestra di comando facendo clic **su Start** e quindi **su Esegui.**

2. Digitare `regedit` nella finestra di **dialogo** Esegui e fare clic su **OK.**

3. Espandere il **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio.**

::: moniker range="vs-2017"

4. Fare clic con il pulsante **destro del mouse sul nodo 15.0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. Fare clic con il pulsante **destro del mouse sul nodo 16.0** e creare una nuova **chiave** denominata `Data Designers` .

::: moniker-end

5. Fare clic con il pulsante **destro del mouse sul nodo Data Designers** (Finestre di progettazione dati) e creare tre nuovi valori stringa:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. Fare clic con il pulsante **destro del mouse sull'elemento SmartCaptionExpression** e **scegliere Modifica.**

7. Immettere `(.*)` per il valore. Corrisponderà all'intera stringa.

8. Fare clic con il pulsante **destro del mouse sull'elemento SmartCaptionReplacement** e **scegliere Modifica.**

9. Immettere `$1` per il valore. In questo modo la stringa viene sostituita con il valore corrispondente, ovvero l'intera stringa in modo che rimanga invariata.

    La volta successiva che si trascinano elementi dalla **finestra Origini** dati, le etichette della didascalia vengono create con didascalie non modificati.

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
