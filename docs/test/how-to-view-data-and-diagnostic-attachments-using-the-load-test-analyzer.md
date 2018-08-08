---
title: Visualizzare gli allegati di dati e diagnostica per i test di carico in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, data and diagnostics attachments
ms.assetid: 73309bdd-437a-4eb0-88c8-702c3e24b9b0
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 228f8306b803fcbd0e83e23e5b8e919dc2116c37
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382464"
---
# <a name="how-to-view-data-and-diagnostic-attachments-using-the-load-test-analyzer"></a>Procedura: Visualizzare allegati di diagnostica e dati usando l'Analizzatore test di carico

Prima di eseguire un test di carico, è possibile selezionare un'impostazione di test che specifichi gli adattatori dati e diagnostico da utilizzare. Dopo aver completato il test di carico, usare l'**Analizzatore test di carico** per visualizzare i dettagli degli adattatori dati e diagnostica durante l'analisi dei risultati. Per visualizzare i dettagli relativi agli adattatori dati e diagnostica, scegliere il pulsante **Visualizza allegati di dati e diagnostica** nella barra degli strumenti dell'**Analizzatore test di carico**. Se ad esempio nell'impostazione per il test di carico era stato configurato l'adattatore per le informazioni sul sistema, è possibile visualizzare le informazioni sul sistema per il computer utilizzato al momento dell'esecuzione del test di carico.

![Finestra di dialogo Seleziona allegato dell'adattatore dati di diagnostica](../test/media/load_adapterdialog.png)

Un altro esempio è un test di carico che include l'adattatore IntelliTrace nell'impostazione di test. L'adattatore IntelliTrace consente di aprire la pagina di **riepilogo di IntelliTrace**.

![Riepilogo di IntelliTrace](../test/media/load_intellitrace.png)

Per altre informazioni, vedere [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md) e [Raccogliere dati IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).

## <a name="to-view-data-and-diagnostic-attachments-in-a-load-test-from-the-load-test-analyzer"></a>Per visualizzare allegati di dati e diagnostica in un test di carico dall'analizzatore test di carico

1.  Dopo il completamento di un test di carico o dopo avere aperto i risultati di un test di carico, nella barra degli strumenti dell'**Analizzatore test di carico** scegliere **Visualizza allegati di dati e diagnostica**.

     Viene visualizzata la finestra di dialogo **Seleziona allegato dell'adattatore dati di diagnostica**.

2.  Selezionare l'allegato dell'adattatore dati di diagnostica che si vuole analizzare, quindi scegliere **OK**.

## <a name="see-also"></a>Vedere anche

- [Analizzare i risultati dei test di carico](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
