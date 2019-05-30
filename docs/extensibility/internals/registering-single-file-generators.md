---
title: La registrazione di generatori di File singoli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b0c3bf7c8260506eabf56113992c985e1cc8669
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351015"
---
# <a name="registering-single-file-generators"></a>Registrazione di generatori di file singoli
Per rendere disponibili in uno strumento personalizzato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario registrarlo così [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possibile crearne un'istanza e la associa a un particolare tipo di progetto.

### <a name="to-register-a-custom-tool"></a>Per registrare uno strumento personalizzato

1. Registrare il DLL dello strumento personalizzato sia nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registro di sistema locale o nel Registro di sistema in HKEY_CLASSES_ROOT.

    Ad esempio, ecco le informazioni di registrazione per lo strumento personalizzato a MSDataSetGenerator gestito, che viene fornito con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Creare una chiave del Registro di sistema nell'oggetto desiderato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive in generatori\\*GUID* in cui *GUID* è il GUID definito dal sistema di progetto o un servizio del linguaggio specifico. Il nome della chiave diventa il nome a livello di uno strumento personalizzato. La chiave degli strumenti personalizzate presenta i seguenti valori:

   - (Predefinito)

        Facoltativo. Fornisce una descrizione intuitiva dello strumento personalizzato. Questo parametro è facoltativo ma consigliato.

   - CLSID

        Obbligatorio. Specifica l'identificatore della libreria di classi del componente COM che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.

   - GeneratesDesignTimeSource

        Obbligatorio. Indica se i tipi dai file generati da questo strumento personalizzato vengono resi disponibili per finestre di progettazione visiva. Il valore di questo parametro deve essere (zero) 0 per i tipi non è disponibili per finestre di progettazione visiva o 1 (uno) per i tipi disponibili per finestre di progettazione visiva.

   > [!NOTE]
   > È necessario registrare lo strumento personalizzato separatamente per ogni lingua per il quale si desidera che lo strumento personalizzato sia disponibile.

    Ad esempio, il MSDataSetGenerator si registra una sola volta per ogni lingua:

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [Implementazione di generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)
- [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [Introduzione all'oggetto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)