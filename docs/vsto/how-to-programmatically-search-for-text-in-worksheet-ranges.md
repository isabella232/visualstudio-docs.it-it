---
title: 'Procedura: eseguire la ricerca a livello di codice per il testo negli intervalli del foglio di lavoro'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c0dcf2787706de121fba691edaf42e9971747524
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920079"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Procedura: eseguire ricerche a livello di codice per il testo negli intervalli del foglio di lavoro
  Il <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> metodo di <xref:Microsoft.Office.Interop.Excel.Range> consente di cercare testo all'interno dell'intervallo. Questo testo può anche essere una delle stringhe di errore che possono essere visualizzati in una cella di foglio di lavoro, ad esempio `#NULL!` o `#VALUE!`. Per altre informazioni sulle stringhe di errore, vedere [i valori di errore delle celle](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Nell'esempio seguente cerca un intervallo denominato `Fruits` e modifica il tipo di carattere per le celle che contengono la parola "mele". Questa procedura Usa anche il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodo, che usa configurate in precedenza impostazioni per ripetere la ricerca di ricerca. Specificare la cella dopo il quale eseguire la ricerca e il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> gestisca il resto.  
  
> [!NOTE]  
>  Il <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> ricerca del metodo esegue il wrapping all'inizio dell'intervallo di ricerca quando viene raggiunta la fine dell'intervallo. Il codice deve verificare che la ricerca non è possibile disporre tutto in un ciclo infinito. La procedura di esempio illustra un modo per gestire questo problema mediante i <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> proprietà.  
  
 ![collegamento a video](../vsto/media/playvideo.gif "collegamento a video") per una dimostrazione video correlata, vedere [How do i: usare il metodo di ricerca in un componente aggiuntivo di Excel?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>Per cercare testo in un intervallo di foglio di lavoro  
  
1. Dichiarare le variabili per l'intero intervallo, il primo intervallo e intervallo trovato corrente di rilevamento.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. Cercare la prima corrispondenza, che specifica tutti i parametri tranne la cella per la ricerca.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. Continuare la ricerca fino a quando sono presenti corrispondenze.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. Confrontare il primo intervallo (`firstFind`) per **Nothing**. Se `firstFind` intervallo trovato non contiene alcun valore, i codice consente di memorizzare (`currentFind`).  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. Se l'indirizzo dell'intervallo trovato corrisponde all'indirizzo del primo intervallo individuato, uscire dal ciclo.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. Impostare l'aspetto dell'intervallo trovato.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. Eseguire un'altra ricerca.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   L'esempio seguente mostra il metodo completo.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Vedere anche  
 [Lavorare con intervalli](../vsto/working-with-ranges.md)   
 [Procedura: a livello di programmazione applicare stili agli intervalli in cartelle di lavoro](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: fare riferimento a livello di programmazione agli intervalli di foglio di lavoro nel codice](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  