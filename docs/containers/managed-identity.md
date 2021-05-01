---
title: Come usare l'identità gestita con Bridge to Kubernetes
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Informazioni su come usare l'identità Azure Active Directory (Azure AD) in un cluster del servizio Bridge to Kubernetes
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335091"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Usare l'identità gestita con Bridge to Kubernetes

Se il cluster [](/azure/active-directory/managed-identities-azure-resources/overview) del servizio AKS usa le funzionalità di sicurezza delle identità gestite per proteggere l'accesso a segreti e risorse, Bridge to Kubernetes richiede una configurazione speciale per garantire che possa funzionare con queste funzionalità. Un token Azure Active Directory (AD) deve essere scaricato nel computer locale per garantire che l'esecuzione e il debug locali siano protetti correttamente e ciò richiede una configurazione speciale in Bridge to Kubernetes. Questo articolo illustra come configurare Bridge to Kubernetes usare i servizi che usano l'identità gestita.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>Come configurare il servizio per l'uso dell'identità gestita

Per abilitare un computer locale con supporto per l'identità gestita, aggiungere nella sezione nel file *KubernetesLocalConfig.yaml* `enableFeatures` `ManagedIdentity` . Aggiungere la `enableFeatures` sezione se non è già presente.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Assicurarsi di usare l'identità gestita solo per Bridge to Kubernetes quando si usano cluster di sviluppo, non cluster di produzione, perché il token Azure AD viene recuperato nel computer locale, che presenta un potenziale rischio per la sicurezza.

Se non si ha un file *KubernetesLocalConfig.yaml,* è possibile crearne uno. Vedere [Procedura: Configurare Bridge to Kubernetes](configure-bridge-to-kubernetes.md).

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Come recuperare i Azure Active Directory token

È necessario assicurarsi di basarsi su o <xref:Azure.Identity.DefaultAzureCredential> nel codice quando si recupera il <xref:Azure.Identity.ManagedIdentityCredential> token.

Il codice C# seguente illustra come recuperare le credenziali dell'account di archiviazione quando si usa `ManagedIdentityCredential` :

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Il codice seguente illustra come recuperare le credenziali dell'account di archiviazione quando si usa DefaultAzureCredential:

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Per informazioni su come accedere ad altre risorse di Azure usando l'identità gestita, vedere la [sezione Passaggi](#next-steps) successivi.

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>Ricevere avvisi di Azure quando vengono scaricati i token

Ogni volta che Bridge to Kubernetes in un servizio, il token Azure AD viene scaricato nel computer locale. È possibile abilitare gli avvisi di Azure per ricevere una notifica in questo caso. Per informazioni, vedere [Abilitare Azure Defender](/azure/security-center/enable-azure-defender). Tenere presente che è presente un addebito (dopo un periodo di valutazione di 30 giorni).

## <a name="next-steps"></a>Passaggi successivi

Ora che è stato configurato il Bridge to Kubernetes per l'uso con il cluster del servizio Web Diaks che usa l'identità gestita, è possibile eseguire il debug come di consueto. Vedere [bridge-to-kubernetes.md#connect-to-your-cluster-and-debug-a-service].

Per altre informazioni sull'uso dell'identificazione gestita per accedere alle risorse di Azure, seguire queste esercitazioni:

- [Esercitazione: Usare un'identità gestita assegnata dal sistema per una macchina virtuale Linux per accedere ad Archiviazione di Azure](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [Esercitazione: Usare un'identità gestita assegnata dal sistema per una macchina virtuale Linux per accedere ad Azure Data Lake Store](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [Esercitazione: Usare un'identità gestita assegnata dal sistema per una macchina virtuale Linux per accedere ad Azure Key Vault](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

In questa sezione sono disponibili altre esercitazioni per l'uso dell'identità gestita per accedere ad altre risorse di Azure.

## <a name="see-also"></a>Vedi anche

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
