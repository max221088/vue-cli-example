<template>
    <footer class="footer">
        <div class="footer-container">
            <div class="active-rows">
                <p class="rows-num">1-5 of 23</p>
            </div>
            <div class="page-navigation">
                <p class="rows-page">Rows per page:</p>
                <select class="select-row">
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                    <option>4</option>
                    <option>5</option>
                </select>
                <img src="../assets/icons/left_icon.svg" class="btn-nav" />
                <img src="../assets/icons/right_icon.svg" class="btn-nav" />
            </div>
        </div>
    </footer>
</template>

<script>
export default {
  name: 'TheFooter'
}
</script>
