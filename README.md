<!DOCTYPE html>
<html>

<head>
  <style >
    body {
     background-color: NavajoWhite;
	text-align: center;
  font-size: 23px;
    }
      </style>
    <meta charset="UTF-8">
    <title>Quadratic Equation Solver</title>


    <script>
        var a, b, c;
        var eqnStr, myDiv;

        // ax^2 + bx + c = 0;
        function getInput() {
            var valid;

            // validate a
            while (!valid) {
                a = prompt("Input 'a' (cannot equal zero) (ax\u00B2 + bx + c)", "1");
                valid = a != 0 && !isNaN(a) && a != null && a != "";
            }

            // validate b
            valid = false;
            while (!valid) {
                b = prompt("Input 'b' (" + (a == 1 ? "" : a) + "x\u00B2 + bx + c)", "6");
                valid = !isNaN(b) && b != null && b != "";
            }

            // validate c
            valid = false;
            while (!valid) {
                c = prompt("Input 'c' (" + (a == 1 ? "" : a) + "x\u00B2 + " + (b == 1 ? "" : b) + "x + c)", "5");
                valid = !isNaN(c) && c != null && c != "";
            }

            // show equation
            myDiv = document.getElementById("my_div");
            showEquation();
            showWorking();
        }

        function showEquation() {
            eqnStr = (a == 1 ? "" : a) + "x\u00B2 + " + (b == 1 ? "" : b) + "x + " + c + " = 0";
            myDiv.innerHTML = "<p>Given the equation <strong>" + eqnStr + "</strong>, we can solve for x by completing the square.</p>";
        }

        function showWorking() {

            // step 1 - divide the equation by a if a doesn't equal 1
            b = b / a;
            c = c / a;
            myDiv.innerHTML = myDiv.innerHTML + "<h4>Step 1 - divide the equation by <em>a</em> (if <em>a</em> doesn't equal 1)</h4><p>" + eqnStr + (a == 1 ? "" : "<br>" + "x\u00B2 + " + (b == 1 ? "" : b) + "x + " + c + " = 0") + "</p>";

            // step 2 - add the square of half of b to both sides
            var halfb = b / 2;
            var halfbSqr = halfb * halfb;
            myDiv.innerHTML = myDiv.innerHTML + "<h4>Step 2 - add the square of half of <em>b</em> to both sides</h4><p>x\u00B2 + " + (b == 1 ? "" : b) + "x + ("+ halfb + ")\u00B2 + " + c + " = (" + halfb + ")\u00B2<br>x\u00B2 + " + (b == 1 ? "" : b) + "x + "+ halfbSqr + " + " + c + " = " + halfbSqr + "</p>";

            // step 3 - convert to the square form, i.e. (x + j)^2 + k;
            myDiv.innerHTML = myDiv.innerHTML + "<h4>Step 3 - convert to the square form</h4><p>(x\u00B2 + " + (b == 1 ? "" : b) + "x + " + halfbSqr + ") + " + c + " = " + halfbSqr + "<br>(x + " + halfb + ")\u00B2 + " + c + " = " + halfbSqr + "</p>";

            // step 4 - solve for x
            var rhs = halfbSqr - c;
            var sqrtRhs = Math.sqrt(rhs);
            myDiv.innerHTML = myDiv.innerHTML + "<h4>Step 4 - solve for <em>x</em></h4><p>(x + " + halfb + ")\u00B2 + " + c + " = " + halfbSqr + "<br>(x + " + halfb + ")\u00B2 = " + rhs + "<br>x + " + halfb + " = \u00B1" + sqrtRhs + "<br>x = " + (-sqrtRhs - halfb) + " or " + (sqrtRhs - halfb) + "</p>";
        }

    </script>
</head>

<body onload="getInput();">
    <div id="my_div"/>
</body>

</html>
