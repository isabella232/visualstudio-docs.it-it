---
title: Come ClickOnce esegue gli aggiornamenti delle applicazioni | Microsoft Docs
description: Informazioni su ClickOnce informazioni sulla versione del file per decidere se aggiornare l'applicazione. ClickOnce l'applicazione di patch ai file per evitare ridondanza durante il download.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 046348ed2f6e8425434291454bb2162aac5c0f82
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128052"
---
# <a name="how-clickonce-performs-application-updates"></a>Come vengono eseguiti gli aggiornamenti di applicazioni con ClickOnce
ClickOnce le informazioni sulla versione del file specificate nel manifesto di distribuzione di un'applicazione per decidere se aggiornare i file dell'applicazione. Dopo l'inizio di un aggiornamento, ClickOnce una tecnica denominata *applicazione di patch* ai file per evitare il download ridondante dei file dell'applicazione.

## <a name="file-patching"></a>Applicazione di patch ai file
 Quando si aggiorna un'applicazione, ClickOnce scarica tutti i file per la nuova versione dell'applicazione, a meno che i file non siano stati modificati. Confronta invece le firme hash dei file specificati nel manifesto dell'applicazione corrente con le firme nel manifesto per la nuova versione. Se le firme di un file sono diverse, ClickOnce scarica la nuova versione. Se le firme corrispondono, il file non è stato modificato da una versione a quella successiva. In questo caso, ClickOnce il file esistente e lo usa nella nuova versione dell'applicazione. Questo approccio impedisce ClickOnce di dover scaricare nuovamente l'intera applicazione, anche se sono stati modificati solo uno o due file.

 L'applicazione di patch ai file funziona anche per gli assembly scaricati su richiesta usando i <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> metodi e <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> .

 Se si usa Visual Studio per compilare l'applicazione, verranno generate nuove firme hash per tutti i file ogni volta che si ricompila l'intero progetto. In questo caso, tutti gli assembly verranno scaricati nel client, anche se è possibile che siano stati modificati solo alcuni assembly.

 L'applicazione di patch ai file non funziona per i file contrassegnati come dati e archiviati nella directory dei dati. Vengono sempre scaricati indipendentemente dalla firma hash del file. Per altre informazioni sulla directory dei dati, vedere Accedere ai dati locali e remoti [nelle ClickOnce applicazioni](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Vedi anche
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)