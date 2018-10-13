---
title: Personalizzare come Visual Studio crea le didascalie per controlli con associazione a dati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf3d47c4e14606a4d3cc3006735fbe04af809600
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195611"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizzare la modalità in cui in Visual Studio vengono create didascalie per controlli con associazione a dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Quando si trascinano elementi dal [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) nella finestra di progettazione Windows Form, entra in gioco una particolare attenzione: i nomi delle colonne nelle etichette della didascalia vengono riformattati in una stringa più leggibile quando due o più parole sono sembra essere concatenati tra loro. È possibile personalizzare il modo in cui vengono create queste etichette, impostando il **SmartCaptionExpression**, **SmartCaptionReplacement**, e **SmartCaptionSuffix** valori in il **progettisti HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Data** chiave del Registro di sistema.  
  
> [!NOTE]
>  Questa chiave del Registro di sistema non esiste fino a quando non si crea.  
  
 I sottotitoli intelligente è controllato dall'espressione regolare immessa nel valore del **SmartCaptionExpression** valore. Aggiunta il **progettazione visiva di dati** chiave del Registro di sistema esegue l'override dell'espressione regolare predefinita che controlla le etichette della didascalia. Per altre informazioni sulle espressioni regolari, vedere [uso di espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 La tabella seguente descrive i valori del Registro di sistema che controllano le etichette della didascalia.  
  
|Elemento Registro di sistema|Descrizione|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|L'espressione regolare usata per la corrispondenza dei modelli.|  
|**SmartCaptionReplacement**|Il formato per visualizzare tutti i gruppi di una corrispondenza con il **SmartCaptionExpression**.|  
|**SmartCaptionSuffix**|Stringa facoltativa da aggiungere alla fine della didascalia.|  
  
 La tabella seguente elenca le impostazioni predefinite interne per questi valori del Registro di sistema.  
  
|Elemento Registro di sistema|Valore predefinito|Descrizione|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu})&#124;_ +|Corrisponde a una lettera minuscola seguita da una lettera maiuscola o un carattere di sottolineatura.|  
|**SmartCaptionReplacement**|$1 $2|$1 rappresenta tutti i caratteri corrispondenti nella prima delle parentesi dell'espressione e il $2 rappresenta tutti i caratteri parentesi secondo una corrispondenza. La sostituzione è la prima corrispondenza, uno spazio e quindi la seconda corrispondenza.|  
|**SmartCaptionSuffix**|:|Rappresenta un carattere aggiunto alla stringa restituita. Ad esempio, se la didascalia è `Company Name`, rende il suffisso `Company Name:`|  
  
> [!CAUTION]
>  È necessario prestare molta attenzione quando si esegue alcuna operazione nell'Editor del Registro di sistema. Eseguire il backup del Registro di sistema prima di modificarlo. Se si usa l'Editor del Registro di sistema in modo non corretto, si possono causare gravi problemi che potrebbero richiedere la reinstallazione del sistema operativo. Microsoft non garantisce che sia possono risolvere i problemi derivanti utilizzando l'Editor del Registro di sistema in modo non corretto. L'utilizzo dell'editor del Registro di sistema è a rischio dell'utente.  
>   
>  L'articolo della Knowledge Base seguente contiene istruzioni per il backup, la modifica e il ripristino del Registro di sistema: [descrizione del Registro di sistema Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Per modificare il comportamento di sottotitoli codificato intelligente della finestra Origini dati  
  
1.  Aprire una finestra di comando facendo **avviare** e quindi **eseguire**.  
  
2.  Tipo di `regedit` nella **eseguire** nella finestra di dialogo e fare clic su **OK**.  
  
3.  Espandere la **HKEY_CURRENT_USER** nodo.  
  
4.  Espandere la **Software** nodo.  
  
5.  Espandere la **Microsoft** nodo.  
  
6.  Espandere la **VisualStudio** nodo.  
  
7.  Fare doppio clic il **10.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.  
  
8.  Fare doppio clic il **progettazione visiva di dati** nodo e creare un nuovo **valore stringa** denominato `SmartCaptionExpression`.  
  
9. Fare doppio clic il **progettazione visiva di dati** nodo e creare un nuovo **valore stringa** denominato `SmartCaptionReplacement`.  
  
10. Fare doppio clic il **progettazione visiva di dati** nodo e creare un nuovo **valore stringa** denominato `SmartCaptionSuffix`.  
  
11. Fare doppio clic il **SmartCaptionExpression** e selezionare**Modify**.  
  
12. Immettere l'espressione regolare desidera che il **Zdroje dat** finestra da utilizzare.  
  
13. Fare doppio clic il **SmartCaptionReplacement** e selezionare**Modify**.  
  
14. Immettere la sostituzione stringa formattati nel modo desiderato visualizzare i modelli di corrispondenza nell'espressione regolare.  
  
15. Fare doppio clic il **SmartCaptionSuffix** e selezionare**Modify**.  
  
16. Immettere eventuali caratteri che si desidera venga visualizzato alla fine della didascalia.  
  
     La volta successiva che si trascinano elementi dal **Zdroje dat** finestra, le etichette della didascalia vengono create utilizzando i nuovi valori del Registro di sistema specificati.  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>Per disattivare la funzionalità smart i sottotitoli codificata  
  
1.  Aprire una finestra di comando facendo **avviare** e quindi **eseguire**.  
  
2.  Tipo di `regedit` nella **eseguire** nella finestra di dialogo e fare clic su **OK**.  
  
3.  Espandere la **HKEY_CURRENT_USER** nodo.  
  
4.  Espandere la **Software** nodo.  
  
5.  Espandere la **Microsoft** nodo.  
  
6.  Espandere la **VisualStudio** nodo.  
  
7.  Fare doppio clic il **10.0** nodo e creare un nuovo **chiave** denominato `Data Designers`.  
  
8.  Fare doppio clic il **progettazione visiva di dati** nodo e creare un nuovo **valore stringa** denominato `SmartCaptionExpression`.  
  
9. Fare doppio clic il **progettazione visiva di dati** nodo e creare un nuovo **valore stringa** denominato `SmartCaptionReplacement`.  
  
10. Fare doppio clic il **progettazione visiva di dati** nodo e creare un nuovo **valore stringa** denominato `SmartCaptionSuffix`.  
  
11. Fare doppio clic il **SmartCaptionExpression** e selezionare**Modify**.  
  
12. Immettere `(.*)` per il valore. Ciò corrisponderà alla stringa intera.  
  
13. Fare doppio clic il **SmartCaptionReplacement** e selezionare**Modify**.  
  
14. Immettere `$1` per il valore. Ciò sostituisce la stringa con il valore corrispondente, ovvero l'intera stringa in modo che rimarrà invariata.  
  
     La volta successiva che si trascinano elementi dal **Zdroje dat** finestra, le etichette della didascalia vengono create con sottotitoli in lingua originale non modificate.  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

