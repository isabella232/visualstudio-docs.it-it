---
title: 'CA1063: implementare IDisposable correttamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04691d2344b232906676180122ad67fff5405891
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539360"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementare IDisposable correttamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 `IDisposable`non è implementato correttamente. Di seguito sono elencati alcuni motivi per questo problema:

- IDisposable viene nuovamente implementato nella classe.

- Finalize viene nuovamente sottoposto a override.

- Viene eseguito l'override di Dispose.

- Dispose () non è Public, sealed o denominato Dispose.

- Dispose (bool) non è protetto, virtuale o non sealed.

- Nei tipi non sealed, Dispose () deve chiamare Dispose (true).

- Per i tipi non sealed, l'implementazione di Finalize non chiama né sia Dispose (bool) né il finalizzatore della classe case.

  La violazione di uno di questi modelli attiverà questo avviso.

  Ogni tipo IDisposable radice non sealed deve fornire il proprio metodo protected virtual void Dispose (bool). Dispose () deve chiamare Dispose (true) e Finalize deve chiamare Dispose (false). Se si sta creando un tipo IDisposable radice non sealed, è necessario definire Dispose (bool) e chiamarlo. Per ulteriori informazioni, vedere la pagina relativa alla [pulizia delle risorse non gestite](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) nella sezione [linee guida di progettazione del Framework](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) della documentazione .NET Framework.

## <a name="rule-description"></a>Descrizione della regola
 È necessario che tutti i tipi IDisposable implementino correttamente il modello Dispose.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare il codice e determinare quale delle risoluzioni seguenti risolverà la violazione.

- Rimuovere IDisposable dall'elenco di interfacce implementate da {0} ed eseguire l'override dell'implementazione Dispose della classe di base.

- Rimuovere il finalizzatore dal tipo {0} , eseguire l'override di Dispose (bool disposing) e inserire la logica di finalizzazione nel percorso del codice dove ' disposing ' è false.

- Rimuovere {0} , eseguire l'override di Dispose (bool disposing) e inserire la logica di Dispose nel percorso del codice dove ' disposing ' è true.

- Verificare che {0} sia dichiarato public e sealed.

- Rinominare {0} in ' Dispose ' e verificare che sia dichiarato public e sealed.

- Verificare che {0} sia dichiarato come protected, Virtual e unsealed.

- Modificare in {0} modo che chiami Dispose (true), quindi chiama GC. SuppressFinalize sull'istanza dell'oggetto corrente (' This ' o ' me ' in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), quindi restituisce.

- Modificare in {0} modo che chiami Dispose (false) e quindi restituisca.

- Se si scrive una classe IDisposable radice non sealed, assicurarsi che l'implementazione di IDisposable segua il modello descritto in precedenza in questa sezione.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="pseudo-code-example"></a>Esempio di pseudocodice
 Lo pseudo-codice seguente fornisce un esempio generale di implementazione di Dispose (bool) in una classe che utilizza risorse gestite e native.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```
