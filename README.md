# wordpressNav

Wordpress twentytwentythree theme different screen size on navigation menu of submenu position outsiding problem. [Solved] AUTO POSTİONG SUBMENUS </br></br>

Wordpress navigation submenu outside problem [solved]</br></br>
Auto positiong of submenus Wordpress twentytwentythree</br></br>
<strong>Solving is : </strong></br>
<p>Create or change file : <i>yourdomain.com/wp-content/themes/twentytwentythree/functions.php</i> AND Copy, paste this code in <i>functions.php</i> </p></br></br>
<code>
<?php 
function addFooter(){
?>
<style>
.rightControl {right:0px  !important; left:auto !important;}
.lastNavLiElement {left: -100% !important;}
</style>
<script>
function subMenuPositionControl() {
    var cS = 200; // body.width - 200
    var lCS = 250; // Last nav li child of no submenu center position
    var bWidth = document.body.clientWidth; // Body width
    var classController = 'rightControl'; // [(Add or Remove) Style Class]
    var classIsLastItem = 'lastNavLiElement'; // for Last nav item [(Add or Remove) Style Class]
    var classSubMenusLi = '.wp-block-navigation-submenu'; class name of if navigation li has submenu 
    var classSubMenuContentUl = '.wp-block-navigation__submenu-container'; // submenu container class name
    document.querySelectorAll(classSubMenusLi).forEach(function(menu, mi) { // mi = index
        if (mi % 2 == 0) { // % without submenu selection 
            console.log(mi); // % log menu index number
            if (bWidth - menu.getBoundingClientRect()['right'] <= cS) { 
                console.log('+');  //  Right positioning of submenu  
                menu.querySelectorAll(classSubMenuContentUl)[0].classList.add(classController);
            } else {
                console.log('-'); //  Left positioning of submenu  
                menu.querySelectorAll(classSubMenuContentUl)[0].classList.remove(classController);
            }
        }
    });
    
    // Last nav li item submenu positon center <<<<<<<İF LAST ITEM!!>>>>>>
    
    var navLastLiItem = document.querySelectorAll(classSubMenusLi)[document.querySelectorAll(classSubMenusLi).length - 2];
    if (navLastLiItem.getBoundingClientRect()['left'] <= lCS) {
        navLastLiItem.querySelectorAll(classSubMenuContentUl)[0].classList.add(classIsLastItem);
    } else {
        navLastLiItem.querySelectorAll(classSubMenuContentUl)[0].classList.remove(classIsLastItem);
    }
}
window.onresize = function() {
    subMenuPositionControl();
};
subMenuPositionControl();</script>
<?php
}
add_action( 'wp_footer', 'addFooter' );
?>
</code>

Screenshot is attached</br></br>
<img src='https://github.com/ayhanhzr/wordpressNav/blob/main/ss.png' />
<strong>Search keywords group for searching :</strong> Wordpress Twentytwentythree theme navigation sub menu problem / issuue, Wordpress Twentytwentythree theme navigation not working, Wordpress Twentytwentythree theme navigation submenu auto positiong 
