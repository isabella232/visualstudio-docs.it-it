---
title: Come ClickOnce esegue gli aggiornamenti dell'applicazione | Microsoft Docs
description: Informazioni su come ClickOnce usa le informazioni sulla versione del file per decidere se aggiornare l'applicazione. ClickOnce usa l'applicazione di patch per evitare la ridondanza durante il download.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0177f199f0178e9fe0221a4cb6daa58d36a6f87
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382667"
---
# <a name="how-clickonce-performs-application-updates"></a>Come vengono eseguiti gli aggiornamenti di applicazioni con ClickOnce
ClickOnce utilizza le informazioni sulla versione del file specificate nel manifesto di distribuzione di un'applicazione per decidere se aggiornare i file dell'applicazione. Dopo l'avvio di un aggiornamento, ClickOnce utilizza una tecnica denominata applicazione di *patch* per evitare il download ridondante dei file dell'applicazione.

## <a name="file-patching"></a>Applicazione di patch ai file
 Quando si aggiorna un'applicazione, ClickOnce non Scarica tutti i file per la nuova versione dell'applicazione, a meno che i file non siano stati modificati. Al contrario, confronta le firme hash dei file specificati nel manifesto dell'applicazione per l'applicazione corrente con le firme nel manifesto per la nuova versione. Se le firme di un file sono diverse, ClickOnce Scarica la nuova versione. Se le firme corrispondono, il file non è stato modificato da una versione a quella successiva. In questo caso, ClickOnce copia il file esistente e lo utilizza nella nuova versione dell'applicazione. Questo approccio impedisce a ClickOnce di dover scaricare di nuovo l'intera applicazione, anche se sono stati modificati solo uno o due file.

 L'applicazione di patch ai file funziona anche per gli assembly scaricati su richiesta mediante i <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> metodi e.

 Se si usa Visual Studio per compilare l'applicazione, vengono generate nuove firme hash per tutti i file ogni volta che si ricompila l'intero progetto. In questo caso, tutti gli assembly verranno scaricati nel client, anche se è possibile che siano stati modificati solo pochi assembly.

 L'applicazione di patch al file non funziona per i file contrassegnati come dati e archiviati nella directory dei dati. Vengono sempre scaricati indipendentemente dalla firma hash del file. Per altre informazioni sulla directory dati, vedere [accedere ai dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Vedere anche
- [Scegliere una strategia di aggiornamento ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)