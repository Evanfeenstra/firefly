<script lang="typescript">
    import { Unit } from '@iota/unit-converter'
    import { Text } from 'shared/components'
    import { formatUnitBestMatch, formatUnitPrecision } from 'shared/lib/units'

    export let color = 'blue' // TODO: profiles will have different colors

    export let balanceRaw = 0
    export let balanceFiat = 0

    let showPreciseBalance = false

    function togglePreciseBalance() {
        showPreciseBalance = !showPreciseBalance
    }
</script>

<div class="flex items-start flex-col flex-wrap space-y-1.5">
    <balance-box
        on:click={togglePreciseBalance}>
        <Text type="h2" overrideColor classes="text-white">
            {showPreciseBalance ? formatUnitPrecision(balanceRaw, Unit.Mi) : formatUnitBestMatch(balanceRaw, true, 3)}
        </Text>
    </balance-box>
    {#if balanceFiat}
        <Text type="p" overrideColor smaller classes="text-{color}-200 dark:text-blue-300">{balanceFiat}</Text>
    {/if}
</div>
