public class PowerUp : MonoBehaviour
{
    public float speedBoost = 2f;
    public float duration = 5f;

    private void OnTriggerEnter2D(Collider2D other)
    {
     
      if (other.CompareTag("Player"))
        {
            StartCoroutine(BoostSpeed(other.GetComponent<PlayerController>()));
            Destroy(gameObject);
        }
    }

    private IEnumerator BoostSpeed(PlayerController player)
    {
        player.speed *= speedBoost;
        yield return new WaitForSeconds(duration);
        player.speed /= speedBoost;
    }
}
