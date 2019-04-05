---
title: (BoundsRules) vincolano posizione e dimensione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d09be82be084767bfb2d300a1877e95456a957b4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966833"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oggetto *regola sui limiti* è una classe che definisce i limiti su dimensioni e la posizione di una forma. Fornisce un metodo che viene chiamato ripetutamente mentre un utente sta trascinando una forma o l'angoli o ai lati di una forma.  
  
 Nell'esempio seguente limita una forma rettangolare sia una barra di dimensioni fisse, orizzontale o verticale. Quando l'utente trascina l'angoli o ai lati, la struttura alternativamente le due configurazioni consentite dell'altezza e larghezza.  
  
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
  
 Si noti che sia la posizione e dimensione può essere vincolate se si desidera.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
