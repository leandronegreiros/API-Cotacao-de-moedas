<template>
    <table class="table">
        <thead>
            <tr>
                <th>Código</th>
                <th>Nome</th>
                <th>Máximo</th>
                <th>Mínimo</th>
                <th>Variação</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(quote, key) in quotes" :key="key">
                <td>{{ key }}</td>
                <td>{{ quote.name }}</td>
                <td>{{ quote.high }}</td>
                <td>{{ quote.low }}</td>
                <td>
                    <span 
                        class="label label-rounded text-smal"
                        :class="{ 'label-error': quote.pctchange < 0, 'label-success':   quote.pctchange > 0}"    
                    >
                        {{ quote.pctChange }} %
                    </span>
                </td>
                <td></td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props: { quotes: { type: Object, requires: true }}
}
</script>