---
title: Più soluzioni DSL in una soluzione unica
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5d21d3954a402e7ce8eb26c34d6a6a5c237309a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658350"
---
# <a name="multiple-dsls-in-one-solution"></a>Più soluzioni DSL in una soluzione unica

È possibile creare un pacchetto di diversi linguaggi specifici di dominio come parte di un'unica soluzione, in modo che vengano installati insieme.

Esistono varie tecniche per integrare più linguaggi specifici di dominio. Per altre informazioni, vedere [integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md) e [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Compilare più di un linguaggio DSL nella stessa soluzione

1. Creare un nuovo progetto **progetto VSIX** .

2. Creare due o più progetti DSL nella directory della soluzione VSIX.

   - Per ogni linguaggio specifico di dominio, aprire una nuova istanza di Visual Studio. Creare il nuovo linguaggio specifico di dominio e specificare la stessa cartella soluzione della soluzione VSIX.

   - Assicurarsi di creare ogni linguaggio specifico di dominio con un'estensione di file diversa.

   - Modificare i nomi dei progetti **DSL** e **DslPackage** in modo che siano tutti diversi. Ad esempio: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - In ogni **DslPackage \* \ source.Extension.TT**aggiornare questa riga con il nome del progetto DSL corretto:

      `string dslProjectName = "Dsl2";`

   - Nella soluzione VSIX aggiungere i progetti DSL * e DslPackage \*. Può essere utile inserire ogni coppia in una specifica cartella soluzione.

2. Combinare i manifesti VSIX dei linguaggi specifici di dominio:

   1. Aprire _progettovsix_ **\Source.Extension.manifest**.

   2. Per ogni DSL, scegliere **Aggiungi contenuto** e aggiungere:

       - `Dsl*` progetto come **componente MEF**

       - `DslPackage*` progetto come **componente MEF**

       - `DslPackage*` progetto come **pacchetto di Visual** Studio

3. Compilare la soluzione.

   Il progetto VSIX risultante installerà entrambi i linguaggi specifici di dominio. È possibile testarli usando F5 oppure distribuire _progettovsix_ **\bin\Debug \\ \*. vsix**.

## <a name="see-also"></a>Vedere anche

- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Procedura: Aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)