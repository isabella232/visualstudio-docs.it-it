---
title: Registrazione di generatori di file singoli Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705803"
---
# <a name="registering-single-file-generators"></a>Registrazione di generatori di file singoli
Per rendere disponibile uno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]strumento personalizzato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , è necessario registrarlo in modo da poterne creare un'istanza e associarlo a un particolare tipo di progetto.

### <a name="to-register-a-custom-tool"></a>Per registrare uno strumento personalizzato

1. Registrare la DLL dello [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] strumento personalizzato nel Registro di sistema locale o nel Registro di sistema, in HKEY_CLASSES_ROOT.

    Ad esempio, ecco le informazioni di registrazione per lo strumento personalizzato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]MSDataSetGenerator gestito, che viene fornito con :

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. Creare una chiave del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registro di\\sistema nell'hive desiderato in*GENERATORi GUID* dove *GUID* è il GUID definito dal sistema di progetto o servizio del linguaggio specifico. Il nome della chiave diventa il nome a livello di codice dello strumento personalizzato. La chiave dello strumento personalizzato ha i seguenti valori:

   - Valore predefinito.

        Facoltativa. Fornisce una descrizione intuitiva dello strumento personalizzato. Questo parametro è facoltativo, ma consigliato.

   - CLSID

        Obbligatorio. Specifica l'identificatore della libreria di classi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>del componente COM che implementa .

   - GeneratesDesignTimeSource (GeneraDesignTimeSource)

        Obbligatorio. Indica se i tipi dei file prodotti da questo strumento personalizzato vengono resi disponibili alle finestre di progettazione visiva. Il valore di questo parametro deve essere (zero) 0 per i tipi non disponibili per le finestre di progettazione visiva o (uno) 1 per i tipi disponibili per le finestre di progettazione visiva.

   > [!NOTE]
   > È necessario registrare lo strumento personalizzato separatamente per ogni lingua per la quale si desidera che lo strumento personalizzato sia disponibile.

    Ad esempio, MSDataSetGenerator registra se stesso una volta per ogni lingua:For example, the MSDataSetGenerator registers itself once for each language:

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
