---
title: Componente React para Dicas
components: Tooltip
---

# Dicas

<p class="description">Dicas exibem texto informativo quando os usuários passam o mouse, focalizam ou tocam em um elemento.</p>

Quando ativada, [dicas](https://material.io/design/components/tooltips.html) exibem um rótulo de texto identificando o elemento, como uma descrição de sua função.

## Dicas simples

{{"demo": "pages/components/tooltips/SimpleTooltips.js"}}

## Posicionamento de dicas

O `Tooltip` tem 12 **posicionamentos** para ser escolhido. Eles não têm setas direcionais; em vez disso, eles dependem do movimento que emana da fonte para transmitir direção.

{{"demo": "pages/components/tooltips/PositionedTooltips.js"}}

## Dicas customizadas

Aqui estão alguns exemplos de customização do componente. Você pode aprender mais sobre isso na [página de documentação de sobrescritas](/customization/components/).

{{"demo": "pages/components/tooltips/CustomizedTooltips.js"}}

## Elemento filho customizado

A dica precisa aplicar ouvintes de evento DOM ao seu elemento filho. Se o filho for um elemento React personalizado, você precisará garantir que ele repasse suas propriedades para o elemento DOM subjacente.

```jsx
function MyComponent (props) {
  // Distribua as propriedades para o elemento DOM subjacente.
  return <div {...props}>Bin</div>
}

// ...

<Tooltip title="Excluir">
  <MyComponent>
</Tooltip>
```

Você pode encontrar um conceito similar no guia de [componentes de encapsulamento](/guides/composition/#wrapping-components).

## Gatilhos

Você pode definir os tipos de eventos que fazem com que uma dica seja exibida.

{{"demo": "pages/components/tooltips/TriggersTooltips.js"}}

## Dicas Controladas

Você pode usas as propriedades `open`, `onOpen` e `onClose` para controlar o comportamento da dica.

{{"demo": "pages/components/tooltips/ControlledTooltips.js"}}

## Largura Variável

A dica (`Tooltip`) quebra o texto longo por padrão para torná-lo legível.

{{"demo": "pages/components/tooltips/VariableWidth.js"}}

## Interativa

Uma dica pode ser interativa. Ela não será fechada quando o usuário passar por cima da dica antes que `leaveDelay` expire.

{{"demo": "pages/components/tooltips/InteractiveTooltips.js"}}

## Elementos Desativados

Por padrão os elementos desativados como `<button>` não disparam interações do usuário, então uma `Tooltip` não será ativada em eventos normais, omo passar o mouse. To accommodate disabled elements, add a simple wrapper element, such as a `span`.

{{"demo": "pages/components/tooltips/DisabledTooltips.js"}}

> Se você não estiver manipulando com um componente Material-UI que herde de `ButtonBase`, por exemplo, um elemento `<button>` nativo, você também deve adicionar a propriedade CSS *pointer-events: none;* ao seu elemento quando desativado:

```jsx
<Tooltip title="Você não tem permissão para esta tarefa">
  <span>
    <button disabled={disabled} style={disabled ? { pointerEvents: "none" } : {}}>
      {'Um botão desabilitado'}
    </button>
  </span>
</Tooltip>
```

## Transições

Use uma transição diferente.

{{"demo": "pages/components/tooltips/TransitionsTooltips.js"}}

## Mostrando e ocultando

A dica normalmente é mostrada imediatamente quando o mouse do usuário passa sobre o elemento e se oculta imediatamente quando o mouse do usuário sai. Um atraso na exibição ou ocultação da dica pode ser adicionado por meio das propriedades `enterDelay` e `leaveDelay`, conforme mostrado na demonstração de dicas controladas acima.

No celular, a dica é exibida quando o usuário pressiona longamente o elemento e oculta após um atraso de 1500 ms. Você pode desativar esse recurso com a propriedade `disableTouchListener`.

{{"demo": "pages/components/tooltips/DelayTooltips.js"}}