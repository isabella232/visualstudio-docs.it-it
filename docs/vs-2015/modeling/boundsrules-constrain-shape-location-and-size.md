---
title: Posizione e dimensioni della forma vincolo BoundsRules | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672723"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una *regola dei limiti* è una classe che definisce i limiti per le dimensioni e la posizione di una forma. Fornisce un metodo che viene chiamato ripetutamente mentre un utente trascina una forma o gli angoli o i lati di una forma.

 L'esempio seguente vincola una forma rettangolare a una barra di dimensioni fisse, orizzontale o verticale. Quando l'utente trascina gli angoli o i lati, il contorno viene invertito tra le due configurazioni consentite di altezza e larghezza.

 La regola dei limiti è una classe derivata da <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Viene creata un'istanza della regola nella forma:

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

 Si noti che, se si desidera, è possibile limitare la posizione e le dimensioni.

## <a name="see-also"></a>Vedere anche
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> la [risposta e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
