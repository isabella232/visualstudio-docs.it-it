---
title: Più DSLs in una soluzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668560"
---
# <a name="multiple-dsls-in-one-solution"></a>Più soluzioni DSL in una soluzione unica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare un pacchetto di diversi linguaggi specifici di dominio come parte di un'unica soluzione, in modo che vengano installati insieme.

 Esistono varie tecniche per integrare più linguaggi specifici di dominio. Per altre informazioni, vedere [integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md) e [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Per compilare più di un linguaggio specifico di dominio nella stessa soluzione

1. Creare due o più soluzioni DSL e un progetto VSIX, quindi aggiungere tutti i progetti a un'unica soluzione.

   - Per creare un nuovo progetto VSIX: nella finestra di dialogo **nuovo progetto** selezionare **Visual C#**, **Extensibility**, **progetto VSIX**.

   - Creare due o più soluzioni DSL nella directory della soluzione VSIX.

        Per ogni linguaggio specifico di dominio, aprire una nuova istanza di Visual Studio. Creare il nuovo linguaggio specifico di dominio e specificare la stessa cartella soluzione della soluzione VSIX.

        Assicurarsi di creare ogni linguaggio specifico di dominio con un'estensione di file diversa.

   - Modificare i nomi dei progetti **DSL** e **DslPackage** in modo che siano tutti diversi. Ad esempio: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - In ogni **DslPackage \* \ source.Extension.TT**aggiornare questa riga al nome del progetto DSL corretto:

        `string dslProjectName = "Dsl2";`

   - Nella soluzione VSIX aggiungere i progetti DSL * e DslPackage \* .

        Può essere utile inserire ogni coppia in una specifica cartella soluzione.

2. Combinare i manifesti VSIX dei linguaggi specifici di dominio:

   1. Aprire _progettovsix_**\Source.Extension.manifest**.

   2. Per ogni DSL, scegliere **Aggiungi contenuto** e aggiungere:

       - `Dsl*` progetto come **componente MEF**

       - `DslPackage*` progetto come **componente MEF**

       - `DslPackage*`progetto come **pacchetto di Visual** Studio

3. Compilare la soluzione.

   Il progetto VSIX risultante installerà entrambi i linguaggi specifici di dominio. È possibile testarli usando F5 oppure distribuire _progettovsix_**\bin\Debug \\ \* . vsix**.

## <a name="see-also"></a>Vedere anche
 [Integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md) [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)
