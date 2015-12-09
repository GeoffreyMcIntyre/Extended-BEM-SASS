# Extended-BEM-SASS
This is an extension and fix of a SASS script I found for outputting in BEM format.

# Description

I originally found a tutorial for making a nice BEM creation script in SASS at (https://medium.com/@marcmintel/pushing-bem-to-the-next-level-with-sass-3-4-5239d2371321#.x8s5v69lk).

There were a few minor things I had to fix, because the script did not work correctly, at least when compiled with gulp which shouldn't make any difference.

I extended it so that selectors can be used to affect subelements. I believe this is valid BEM, there seem to be a mix of opinions on this matter. I am trying to find out which side has the most support.

# How to use

@include b(blockName) {

    @include m(modifierName) {
        
    }
    
    @include e(elementName) {
    
    }
}

## Sample Usage Script

@include b(block) {
    background: red;
    
    @include m(modifier) {
        color: blue;
        
        @include e(subelement) { 
            background: gray;
        }
        
        &:nth-child(odd){
            color: green;

            @include e(subelement) { 
                background: gray;
            }
        }
    }
    
    @include e(element) { 
        background: orange;
        
        @include m(modifier) {
            color: yellow;
            
            &:nth-child(odd){
                color: yellowgreen;

                @include e(subelement) { 
                    background: black;
                }
            }
        }
        
        &:nth-child(odd){
            color: tan;

            @include e(subelement) { 
                background: cyan;
            }
        }
    }
}

## Output

.block {
    background: red;
}

.block--modifier {
    color: blue;
}

.block--modifier .block__subelement {
    background: gray;
}

.block--modifier:nth-child(odd) {
    color: green;
}

.block--modifier:nth-child(odd) .block__subelement {
    background: gray;
}

.block__element {
    background: orange;
}

.block__element--modifier {
    color: yellow;
}

.block__element--modifier:nth-child(odd) {
    color: yellowgreen;
}

.block__element--modifier:nth-child(odd) .block__subelement {
    background: black;
}

.block__element:nth-child(odd) {
    color: tan;
}

.block__element:nth-child(odd) .block__subelement {
    background: cyan;
}
