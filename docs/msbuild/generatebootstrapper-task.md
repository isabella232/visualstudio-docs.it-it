---
title: Attività GenerateBootstrapper | Microsoft Docs
description: Usare l MSBuild generateBootstrapper per un modo automatico per rilevare, scaricare e installare un'applicazione e i relativi prerequisiti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b198b62a7931d2bb88e3194cc8f159d67602c98d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069251"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper (attività)

Consente di rilevare, scaricare e installare automaticamente un'applicazione e i relativi prerequisiti. Funge da programma di installazione singolo che integra i programmi di installazione separati per tutti i componenti che costituiscono un'applicazione.

## <a name="task-parameters"></a>Parametri dell'attività

Di seguito vengono descritti i parametri dell'attività `GenerateBootstrapper`.

- `ApplicationFile`

   Parametro `String` facoltativo.

   Specifica il file che verrà usato dal programma di avvio automatico per iniziare l'installazione dell'applicazione dopo l'installazione di tutti i prerequisiti. Se non si specifica il parametro `BootstrapperItems` o `ApplicationFile`, si verificherà un errore di compilazione.

- `ApplicationName`

   Parametro `String` facoltativo.

   Specifica il nome dell'applicazione che verrà installata dal programma di avvio automatico. Questo nome verrà visualizzato nell'interfaccia utente usata dal programma di avvio automatico durante l'installazione.

- `ApplicationRequiresElevation`

   Parametro `Boolean` facoltativo.

   Se `true`, il componente viene eseguito con autorizzazioni elevate quando viene installato in un computer di destinazione.

- `ApplicationUrl`

   Parametro `String` facoltativo.

   Specifica il percorso Web che ospita il programma di installazione dell'applicazione.

- `BootstrapperComponentFiles`

   Parametro di ouput facoltativo `String[]`.

   Specifica il percorso predefinito dei file di pacchetto del programma di avvio automatico.

- `BootstrapperItems`

   Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.

   Specifica i prodotti da compilare nel programma di avvio automatico. Gli elementi passati a questo parametro devono avere la sintassi seguente:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   L'attributo `Include` rappresenta il nome di un prerequisito che deve essere installato. I metadati dell'elemento `ProductName` sono facoltativi e vengono usati dal motore di compilazione come nome descrittivo se non è possibile trovare il pacchetto. Questi elementi non sono necessari per MSBuild di input, a meno che non `ApplicationFile` venga specificato alcun elemento . È consigliabile includere un elemento per ogni prerequisito che deve essere installato per l'applicazione.

   Se non si specifica il parametro `BootstrapperItems` o `ApplicationFile`, si verificherà un errore di compilazione.

- `BootstrapperKeyFile`

   Parametro di ouput facoltativo `String`.

   Specifica il percorso di compilazione del file *setup.exe*

- `ComponentsLocation`

   Parametro `String` facoltativo.

   Specifica il percorso in cui il programma di avvio automatico esegue la ricerca dei prerequisiti di installazione. Per il parametro è possibile specificare i valori seguenti:

  - `HomeSite`: indica che il prerequisito è ospitato dal fornitore del componente.

  - `Relative`: indica che il prerequisito è nella stessa posizione dell'applicazione.

  - `Absolute`: indica che tutti i componenti devono trovarsi in un URL centralizzato. Questo valore deve essere usato con il parametro di input `ComponentsUrl`.

    Se `ComponentsLocation` non è specificato, per impostazione predefinita viene usato `HomeSite`.

- `ComponentsUrl`

   Parametro `String` facoltativo.

   Specifica l'URL che contiene i prerequisiti di installazione.

- `CopyComponents`

   Parametro `Boolean` facoltativo.

   Se `true`, il programma di avvio automatico copia tutti i file di output nel percorso specificato nel parametro `OutputPath`. I valori del parametro `BootstrapperComponentFiles` devono essere tutti basati su questo percorso. Se `false`, i file non vengono copiati e i valori di `BootstrapperComponentFiles` si basano sul valore del parametro `Path`.  Il valore predefinito di questo parametro è `true`.

- `Culture`

   Parametro `String` facoltativo.

   Specifica le impostazioni cultura da usare per i prerequisiti relativi all'interfaccia utente del programma di avvio automatico e all'installazione. Se le impostazioni cultura specificate non sono disponibili, l'attività usa il valore del parametro `FallbackCulture`.

- `FallbackCulture`

   Parametro `String` facoltativo.

   Specifica le impostazioni cultura secondarie da usare per l'interfaccia utente di avvio e i prerequisiti di installazione.

- `OutputPath`

   Parametro `String` facoltativo.

   Specifica il percorso in cui copiare *setup.exe* e tutti i file di pacchetto.

- `Path`

   Parametro `String` facoltativo.

   Specifica il percorso di tutti i pacchetti dei prerequisiti disponibili.

- `SupportUrl`

   Parametro `String` facoltativo.

   Specifica l'URL da implementare se l'installazione del programma di avvio automatico ha esito negativo.

- `Validate`

   Parametro `Boolean` facoltativo.

   Se `true`, il programma di avvio automatico esegue la convalida XSD sugli elementi del programma di avvio automatico di input specificati. Il valore predefinito di questo parametro è `false`.

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Esempio

L'esempio seguente usa l'attività `GenerateBootstrapper` per installare un'applicazione che deve avere .NET Framework 2.0 installato come prerequisito.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
