<script>
export default {
  
  name: 'slideToggle',
  functional: true,
  render(createElement, context) {
    const data = {
      props: {
        name: 'expand',
        delay: {
          type: Number,
          default: 400
        }
      },
      on: {
        afterEnter(element) {
          // eslint-disable-next-line no-param-reassign
          element.style.height = 'auto';
        },
        enter(element) {
          element.style.transition = `height ${context.props.delay}ms`
          const { width } = getComputedStyle(element);
          /* eslint-disable no-param-reassign */
          element.style.width = width;
          element.style.position = 'absolute';
          element.style.visibility = 'hidden';
          element.style.height = 'auto';
          /* eslint-enable */
          const { height } = getComputedStyle(element);
          /* eslint-disable no-param-reassign */
          element.style.width = null;
          element.style.position = null;
          element.style.visibility = null;
          element.style.height = 0;
          

          /* eslint-enable */
          // Force repaint to make sure the
          // animation is triggered correctly.
          // eslint-disable-next-line no-unused-expressions
          getComputedStyle(element).height;
          setTimeout(() => {
            // eslint-disable-next-line no-param-reassign
            element.style.height = height;
          });
        },
        leave(element) {
          element.style.transition = `height ${context.props.delay}ms`
          const { height } = getComputedStyle(element);
          // eslint-disable-next-line no-param-reassign
          
          element.style.height = height;
          // Force repaint to make sure the
          // animation is triggered correctly.
          // eslint-disable-next-line no-unused-expressions
          getComputedStyle(element).height;
          setTimeout(() => {
            // eslint-disable-next-line no-param-reassign
            element.style.height = 0;
          });
        },
      },
    };
    
    return createElement('transition', data, context.children);
  },
};
</script>

<style scoped>
  * {
    will-change: height;
    transform: translateZ(0);
    backface-visibility: hidden;
    perspective: 1000px;
  }
</style>

<style>
  .expand-enter-active,
  .expand-leave-active {
    /* transition: height .3s ease-in-out; */
    overflow: hidden;
  }

  .expand-enter,
  .expand-leave-to {
    height: 0;
  }
</style>
