---
title: BoundsRules vincolare posizione e dimensione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2474040edc439aad8a9dd75826d4918e6773e186
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme
Oggetto *limiti regola* è una classe che definisce i limiti alle dimensioni e posizione di una forma. Fornisce un metodo che viene chiamato ripetutamente quando un utente sta trascinando una forma o negli angoli o ai lati della forma.  
  
 Nell'esempio seguente viene vincola una forma rettangolare a una barra di dimensioni fisse, orizzontale o verticale. Quando l'utente trascina l'angoli o ai lati, la struttura consente di capovolgere tra le due configurazioni consentite dell'altezza e larghezza.  
  
 I limiti della regola è una classe derivata da <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Viene creata un'istanza della regola nella forma:  
  
```  
using Microsoft.VisualStudio.Modeling.Diagrams; ...  
public partial class BarShape  
{  
  /// <summary>  
  /// Rule invoked when the user is resizing a shape.  
  /// </summary>  
  public override BoundsRules BoundsRules  
  { get { return new BarBoundsRule(); } }  
}  
/// <summary>  
/// Rule invoked when the user is changing a shape's outline.  
/// Provides real-time mouse rubber-band feedback, so must work fast.  
/// </summary>  
public class BarBoundsRule: BoundsRules  
{   
  public override RectangleD GetCompliantBounds   
     (ShapeElement shape, RectangleD proposedBounds)  
  {  
    double thickness = 0.1;  
    if (proposedBounds.Height > proposedBounds.Width)  
    {  
      // There is a minimum width for a shape; the width  
      // will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
            new SizeD(thickness, proposedBounds.Height));  
    }  
    else  
    {  
      // There is a minimum height for a shape; the   
      // height will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
         new SizeD(proposedBounds.Width, thickness));  
} } }  
```  
  
 Si noti che può essere vincolati sia la posizione e dimensioni se si desidera.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)