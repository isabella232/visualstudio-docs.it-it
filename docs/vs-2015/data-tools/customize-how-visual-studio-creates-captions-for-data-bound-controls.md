---
title: Personalizzare il modo in cui Visual Studio 2015 crea le didascalie per i controlli associati a dati | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476923"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si trascinano elementi dalla [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) nel Progettazione Windows Form, si verifica una particolare considerazione: i nomi delle colonne nelle etichette della didascalia vengono riformattati in una stringa più leggibile quando vengono rilevate due o più parole da concatenare insieme. È possibile personalizzare la modalità di creazione di queste etichette, impostando i valori **SmartCaptionExpression**, **SmartCaptionReplacement**e **SmartCaptionSuffix** nella chiave del registro di sistema **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\10.0\Data designer** .

> [!NOTE]
> Questa chiave del registro di sistema non esiste fino a quando non viene creata.

 La didascalia intelligente è controllata dall'espressione regolare immessa nel valore del valore **SmartCaptionExpression** . L'aggiunta della chiave del registro di sistema **Data Designer** sostituisce l'espressione regolare predefinita che controlla le etichette delle didascalie. Per altre informazioni sulle espressioni regolari, vedere [uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 La tabella seguente descrive i valori del registro di sistema che controllano le etichette delle didascalie.

|Elemento del registro di sistema|Descrizione|
|-------------------|-----------------|
|**SmartCaptionExpression**|Espressione regolare usata per trovare la corrispondenza con i criteri.|
|**SmartCaptionReplacement**|Formato per visualizzare i gruppi corrispondenti in **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Stringa facoltativa da aggiungere alla fine della didascalia.|

 Nella tabella seguente sono elencate le impostazioni predefinite interne per questi valori del registro di sistema.

|Elemento del registro di sistema|Valore predefinito|Spiegazione|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) &#124;_+|Corrisponde a un carattere minuscolo seguito da un carattere maiuscolo o un carattere di sottolineatura.|
|**SmartCaptionReplacement**|$1 $2|$1 rappresenta tutti i caratteri corrispondenti nelle prime parentesi dell'espressione e il $2 rappresenta tutti i caratteri corrispondenti nella seconda parentesi. La sostituzione è la prima corrispondenza, uno spazio e quindi la seconda corrispondenza.|
|**SmartCaptionSuffix**|:|Rappresenta un carattere aggiunto alla stringa restituita. Ad esempio, se la didascalia è `Company Name`, il suffisso lo rende `Company Name:`|

> [!CAUTION]
> È necessario prestare molta attenzione quando si esegue qualsiasi operazione nell'editor del registro di sistema. Eseguire il backup del registro di sistema prima di modificarlo. Se si utilizza l'editor del registro di sistema in modo errato, è possibile che si verifichino gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che i problemi causati dall'utilizzo errato dell'editor del registro di sistema possano essere risolti. L'utilizzo dell'editor del Registro di sistema è a rischio dell'utente.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Per modificare il comportamento di Smart Caption della finestra Origini dati

1. Aprire una finestra di comando facendo clic su **Start** , quindi su **Esegui**.

2. Digitare `regedit` nella finestra di dialogo **Esegui** , quindi fare clic su **OK**.

3. Espandere il nodo **HKEY_CURRENT_USER** .

4. Espandere il nodo **software** .

5. Espandere il nodo **Microsoft** .

6. Espandere il nodo **VisualStudio** .

7. Fare clic con il pulsante destro del mouse sul nodo **10,0** e creare una nuova **chiave** denominata `Data Designers`.

8. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare un nuovo **valore stringa** denominato `SmartCaptionExpression`.

9. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare un nuovo **valore stringa** denominato `SmartCaptionReplacement`.

10. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare un nuovo **valore stringa** denominato `SmartCaptionSuffix`.

11. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionExpression** e scegliere **modifica**.

12. Immettere l'espressione regolare che si desidera venga utilizzata dalla finestra **origini dati** .

13. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionReplacement** e scegliere **modifica**.

14. Immettere la stringa di sostituzione formattata nel modo in cui si desidera visualizzare i modelli corrispondenti nell'espressione regolare.

15. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionSuffix** e scegliere **modifica**.

16. Immettere i caratteri che si desidera visualizzare alla fine della didascalia.

     La volta successiva che si trascinano gli elementi dalla finestra **origini dati** , le etichette didascalia vengono create utilizzando i nuovi valori del registro di sistema specificati.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Per disattivare la funzionalità di Smart Caption

1. Aprire una finestra di comando facendo clic su **Start** , quindi su **Esegui**.

2. Digitare `regedit` nella finestra di dialogo **Esegui** , quindi fare clic su **OK**.

3. Espandere il nodo **HKEY_CURRENT_USER** .

4. Espandere il nodo **software** .

5. Espandere il nodo **Microsoft** .

6. Espandere il nodo **VisualStudio** .

7. Fare clic con il pulsante destro del mouse sul nodo **10,0** e creare una nuova **chiave** denominata `Data Designers`.

8. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare un nuovo **valore stringa** denominato `SmartCaptionExpression`.

9. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare un nuovo **valore stringa** denominato `SmartCaptionReplacement`.

10. Fare clic con il pulsante destro del mouse sul nodo **Data Designer** e creare un nuovo **valore stringa** denominato `SmartCaptionSuffix`.

11. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionExpression** e scegliere **modifica**.

12. Immettere `(.*)` per il valore. Corrisponderà all'intera stringa.

13. Fare clic con il pulsante destro del mouse sull'elemento **SmartCaptionReplacement** e scegliere **modifica**.

14. Immettere `$1` per il valore. Questa operazione sostituisce la stringa con il valore corrispondente, ovvero l'intera stringa in modo che rimanga invariata.

     La volta successiva che si trascinano gli elementi dalla finestra **origini dati** , le etichette didascalia vengono create con didascalie non modificate.

## <a name="see-also"></a>Vedere anche
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
