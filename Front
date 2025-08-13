package br.com.dalario.imc

import android.annotation.SuppressLint
import android.os.Bundle
import android.view.Surface
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.compose.foundation.BorderStroke
import androidx.compose.foundation.Image
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.Arrangement
import androidx.compose.foundation.layout.Box
import androidx.compose.foundation.layout.Column
import androidx.compose.foundation.layout.Row
import androidx.compose.foundation.layout.Spacer
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.fillMaxWidth
import androidx.compose.foundation.layout.height
import androidx.compose.foundation.layout.offset
import androidx.compose.foundation.layout.padding
import androidx.compose.foundation.layout.size
import androidx.compose.foundation.layout.width
import androidx.compose.foundation.shape.CircleShape
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.foundation.text.KeyboardOptions
import androidx.compose.material3.Button
import androidx.compose.material3.ButtonDefaults
import androidx.compose.material3.Card
import androidx.compose.material3.CardColors
import androidx.compose.material3.CardDefaults
import androidx.compose.material3.MaterialTheme
import androidx.compose.material3.OutlinedTextField
import androidx.compose.material3.OutlinedTextFieldDefaults
import androidx.compose.material3.Scaffold
import androidx.compose.material3.Surface
import androidx.compose.material3.Text
import androidx.compose.material3.rememberTopAppBarState
import androidx.compose.runtime.Composable
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.draw.clip
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.graphics.RectangleShape
import androidx.compose.ui.layout.ContentScale
import androidx.compose.ui.layout.ModifierLocalBeyondBoundsLayout
import androidx.compose.ui.res.colorResource
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.text.font.FontFamily
import androidx.compose.ui.text.font.FontStyle
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.text.input.KeyboardType
import androidx.compose.ui.text.style.TextAlign
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import androidx.core.graphics.toColorInt
import br.com.dalario.imc.ui.theme.ImcTheme
import kotlinx.serialization.internal.throwMissingFieldException
import java.nio.file.WatchEvent

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            ImcTheme {
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = Color.White
                ) {
                    ImcScreen()
                }
            }
        }
    }
}

@SuppressLint("DefaultLocale")
@Composable
fun ImcScreen() {


    var peso = remember {
        mutableStateOf("")
    }
    var altura = remember {
    mutableStateOf("")
    }

    var imc = remember {
        mutableStateOf(0.0)
    }

    var statusimc = remember {
        mutableStateOf("")
    }
    var corresultado = remember {
        mutableStateOf(value = Color(0xFFED145B))
    }

    Box(
        modifier = Modifier.fillMaxSize(),

    ){
        Column (
            horizontalAlignment = Alignment.CenterHorizontally,
            modifier = Modifier
                .fillMaxWidth()
                .height(160.dp)
                .background(colorResource(R.color.vermelho_fiap)),
        ){
            Spacer(modifier = Modifier.height(30.dp))
            Image(
                painter = painterResource(id = R.drawable.bmi),
                contentDescription = "logo",
                modifier = Modifier
                    .size(60.dp, 60.dp)
                    .clip(shape = CircleShape)
                    .background(color= Color.Gray),
                contentScale = ContentScale.Crop,
            )
           Spacer(modifier = Modifier.height(10.dp))
            Text(
                text = "CALCULADORA IMC",
                color = colorResource(id = R.color.cor_do_texto),
                fontSize = 20.sp,
                fontStyle = FontStyle.Normal,
                fontFamily = FontFamily.Default
            )
        }
        Column(
            modifier = Modifier
                .fillMaxWidth()
                .padding(horizontal = 32.dp)

        ) {
            Spacer(modifier = Modifier.height(130.dp))
            Card(
                //modifier = Modifier.height(300.dp).fillMaxWidth(),
                colors = CardDefaults.cardColors(containerColor = Color.White),
                elevation = CardDefaults.cardElevation(4.dp),
                border = BorderStroke(width = 1.dp, color = Color.Gray),
                shape = RoundedCornerShape(20.dp)
            ){
                Column(
                    modifier = Modifier.padding(
                        vertical = 16.dp,
                        horizontal = 32.dp
                    )
                ) {
                    Text(
                        modifier = Modifier.fillMaxWidth(),
                        textAlign = TextAlign.Center,
                        text = "Seus dados",
                        fontSize = 25.sp,
                        color = colorResource(id= R.color.vermelho_fiap),
                        fontWeight = FontWeight.Bold
                    )
                    Spacer(modifier = Modifier.height(20.dp))
                    Text(
                        "Seu peso",
                        textAlign = TextAlign.Start,
                        fontSize = 15.sp,
                        color = colorResource(id = R.color.vermelho_fiap)
                    )
                    OutlinedTextField(
                        value = peso.value,
                        onValueChange = {peso.value = it},
                        modifier = Modifier.fillMaxWidth(),
                        placeholder = {
                            Text(text ="Seu peso em Kg.", color = Color.Black)

                        },
                        colors = OutlinedTextFieldDefaults.colors(
                            unfocusedBorderColor = colorResource(id = R.color.vermelho_fiap),
                            focusedBorderColor = colorResource(id = R.color.vermelho_fiap),
                            unfocusedTextColor = Color.Black,
                            focusedTextColor = Color.Black
                        ),
                        shape = RoundedCornerShape(15.dp),
                        keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Decimal)
                    )
                    Spacer(modifier = Modifier.height(15.dp))
                    Text(text = "Sua altura",
                        textAlign = TextAlign.Start,
                        fontSize = 15.sp,
                        color = colorResource(id = R.color.vermelho_fiap)
                    )
                    OutlinedTextField(
                        value = altura.value,
                        onValueChange = {
                            altura.value = it
                        },
                        modifier = Modifier.fillMaxWidth(),
                        placeholder = {
                            Text(text="Sua altura em cm.", color = Color.Black)
                        },
                        colors = OutlinedTextFieldDefaults.colors(
                            unfocusedBorderColor = colorResource(id = R.color.vermelho_fiap),
                            focusedBorderColor = colorResource(id = R.color.vermelho_fiap),
                            unfocusedTextColor = Color.Black,
                            focusedTextColor = Color.Black
                        ),
                        shape = RoundedCornerShape(15.dp),
                        keyboardOptions = KeyboardOptions(keyboardType = KeyboardType.Decimal)
                    )
                    Spacer(modifier = Modifier.height(25.dp))
                    Row(horizontalArrangement = Arrangement.SpaceBetween) {
                        Button(
                            onClick = {
                                imc.value =
                                    calcularImc(peso.value.toDouble(), altura.value.toDouble())
                                corresultado.value =
                                    statuscor(statusimc = obterstatusimc(imc.value))

                            },
                            modifier = Modifier.height(48.dp).width(120.dp),
                            colors = ButtonDefaults.buttonColors(colorResource(id = R.color.vermelho_fiap)),
                            shape = RoundedCornerShape(15.dp)
                        ) {
                            Text(
                                "CALCULAR",
                                fontWeight = FontWeight.Bold,
                                color = Color.White,
                                fontSize = 14.sp
                            )
                        }
                        Spacer(modifier = Modifier.width(20.dp))
                        Button(
                            onClick = {corresultado.value = Color(0xFFED145B)
                                        statusimc.value = ""
                                        peso.value = ""
                                        altura.value = ""
                                        imc.value = 0.0
                                      },
                            modifier = Modifier
                                .height(48.dp)
                                .width(220.dp),
                            shape = RoundedCornerShape(15.dp),
                            colors = ButtonDefaults.buttonColors(colorResource(id = R.color.vermelho_fiap))

                        ) {
                            Text(
                                "REINICIAR",
                                color = Color.White,
                                fontWeight = FontWeight.Bold,
                                fontSize = 14.sp
                            )
                        }
                    }
                }
            }
        }
        statusimc.value = obterstatusimc(imc.value)
        Card(
            modifier = Modifier
                .fillMaxWidth()
                .height(height = 200.dp)
                .padding(horizontal = 32.dp, vertical = 24.dp)
              //  .align(Alignment.Center)
                .offset(y= 530.dp),
            colors = CardDefaults.cardColors(containerColor = corresultado.value),
            elevation = CardDefaults.cardElevation(4.dp),
           // 0xFF00E676
        ){
            Row(verticalAlignment = Alignment.CenterVertically,
                modifier = Modifier
                .fillMaxSize()
                .padding(horizontal = 32.dp)
            ){
                Column(){
                    Text(
                        "Resultado",
                        color = Color.White,
                        fontSize = 14.sp
                    )
                    Text(text = statusimc.value,
                        fontWeight = FontWeight.Bold,
                        color = Color.White,
                        fontSize = 14.sp
                        )

                }
                Text(text= String.format("%.1f", imc.value),
                    fontWeight = FontWeight.Bold,
                    color = Color.White,
                    fontSize = 36.sp,
                    textAlign = TextAlign.End,
                    modifier = Modifier.fillMaxWidth())
            }
    }


    }
}
