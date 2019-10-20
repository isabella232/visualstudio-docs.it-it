---
title: Analisi del code coverage nei test di verifica della compilazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2442bf4cc31eeb51332aa28325924e18ccb1ffb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660724"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analisi del code coverage nei test di verifica della compilazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'analisi del code coverage in Microsoft Visual Studio mostra la quantità di codice usato dai test automatizzati. Per altre informazioni, vedere [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

 Quando si controlla il codice, i test vengono eseguiti sul server di compilazione insieme a tutti gli altri test degli altri membri del team. Se questa operazione non è già stata configurata, vedere [eseguire test nel processo di compilazione](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38). È utile analizzare code coverage nel servizio di compilazione, perché fornisce l'immagine più aggiornata e completa del code coverage nell'intero progetto. Vengono inclusi i test di sistema automatizzati e altri test codificati che normalmente non vengono eseguiti nei computer di sviluppo.

1. In Team Explorer aprire **Compilazioni** e aggiungere o modificare una definizione di compilazione.

2. Nella pagina **Processo** espandere **Test automatizzati**, **Origine test**, **Impostazioni esecuzione test**. Impostare **Tipo di file di impostazioni esecuzione test** su **Code coverage abilitato**.

    Se si dispone di più di una definizione di origine del test, ripetere questo passaggio per ciascuna di esse.

   - <em>Non esistono campi denominati **Tipo di file di impostazioni esecuzione test</em>* .*

      In **Test automatizzati** selezionare **Assembly di test** e premere il pulsante con i puntini di sospensione **[...]** alla fine della riga. Nella finestra di dialogo **Aggiungi/Modifica esecuzione dei test** in **Test Runner** scegliere **Visual Studio Test Runner**.

   ![Impostazione della definizione di compilazione per code coverage](../test/media/codecoverage-plaincc.png "Codecover-plainCC")

   Dopo la compilazione, i risultati di code coverage vengono visualizzati nel riepilogo della compilazione.

## <a name="see-also"></a>Vedere anche
 [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
