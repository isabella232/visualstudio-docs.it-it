---
title: Più soluzioni DSL in una soluzione unica
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c894ce7466c253916794495649fa65d703e6d67
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416149"
---
# <a name="multiple-dsls-in-one-solution"></a>Più soluzioni DSL in una soluzione unica

È possibile creare un pacchetto di diversi linguaggi specifici di dominio come parte di un'unica soluzione, in modo che vengano installati insieme.

Esistono varie tecniche per integrare più linguaggi specifici di dominio. Per altre informazioni, vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [come: Aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md) e [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Creare più di un linguaggio specifico di dominio nella stessa soluzione

1. Creare una nuova **progetto VSIX** progetto.

2. Creare due o più progetti DSL nella directory della soluzione VSIX.

   - Per ogni linguaggio specifico di dominio, aprire una nuova istanza di Visual Studio. Creare il nuovo linguaggio specifico di dominio e specificare la stessa cartella soluzione della soluzione VSIX.

   - Assicurarsi di creare ogni linguaggio specifico di dominio con un'estensione di file diversa.

   - Modificare i nomi delle **Dsl** e **DslPackage** progetti in modo che siano tutti diversi. Ad esempio: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - In ognuno **DslPackage\*\source.extension.tt**, aggiornare questa riga con il nome del progetto Dsl corretto:

      `string dslProjectName = "Dsl2";`

   - Nella soluzione VSIX aggiungere i Dsl * e DslPackage\* progetti. Può essere utile inserire ogni coppia in una specifica cartella soluzione.

2. Combinare i manifesti VSIX dei linguaggi specifici di dominio:

   1.  Aprire _Progettovsix_**\source.extension.manifest**.

   2.  Per ogni linguaggio DSL, scegliere **Aggiungi contenuto** e aggiungere:

       -   `Dsl*` il progetto come un **componente MEF**

       -   `DslPackage*` il progetto come un **componente MEF**

       -   `DslPackage*` il progetto come un **pacchetto Visual Studio**

3. Compilare la soluzione.

   Il progetto VSIX risultante installerà entrambi i linguaggi specifici di dominio. È possibile testarli usando F5 oppure distribuire _Progettovsix_**\bin\Debug.\\\*VSIX**.

## <a name="see-also"></a>Vedere anche

- [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Procedura: Aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)