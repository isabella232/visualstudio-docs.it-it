---
title: Valori e parametri non usati
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1ea80887fff6dcb1afba80feb782b23d1e790579
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325026"
---
# <a name="unused-expression-values-and-parameters"></a>Valori e parametri di espressione non usati

Questo refactoring si applica a:

- C#
- Visual Basic

**Cosa:** applica la dissolvenza ai parametri non usati e genera un avviso per i valori di espressione non usati.

**Quando:** si hanno parametri o valori di espressione che non vengono mai usati.

**Perché?:** a volte è difficile stabilire se un parametro o un valore non viene più usato. Applicando la dissolvenza a questi valori o generando un avviso, si ottiene un'indicazione visiva del codice che è possibile eliminare.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostica per valori e parametri di espressione non usati

1. Sono presenti valori di espressione o parametri non usati.
2. Il parametro non usato appare attenuato. Il valore di espressione non usato riceve un avviso.

  ![Parametro non usato](media/unused-parameter.png)
  ![Valore non usato](media/unused-value.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
